# carrot

  call target                                                  call original
      v                                                              |
      |                                                              |
      |       target                              replacement        |       original
      +-> +-----------+                     +-> +-------------+      +---> +----------+
          |    JMP1   | jump to replacement |   |     new     |            |    JMP   |
      +-> +-----------+---------------------+   |    target   |            +----+-----+
      |   |    code   |       (jmp2r)           |     func    |                 |
      |   |    ...    |                         |             |                 |
      |   +-----------+                         +-------------+          jump to bridge
      |   |    JMP2   |                                                         |
      |   +-----------+---------+                                               |
    (jmp2t)                     |                                             (jmp2b)
      |                  jump to incr stack                                     |
      |                       (jmp2i)                                           |
      |          bridge         |                                               |
      |   +----------------+ <--------------+-----------------------------------+
      |   | code from JMP1 |    |           ^
      |   +----------------+    |           |
      |   |    JMP         |    |           |
      +---+----------------+    |  continue exec after stack incrd
          +----------------+ <--+         (jmp2b)
          | call incr stk  |                |
          +----------------+                |
          |       JMP      |                |
          +----------------+----------------+
