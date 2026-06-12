---
title: "About a Bad Ram"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by brodock on 2006-04-03
it's not a question about badram kernel patch but a failure ram module...

i know that one of my ram modules have problems (i did a memtest) but what i'm asking is about the command ps -v
i have an output like this:

```

  PID TTY      STAT   TIME  MAJFL   TRS   DRS   RSS %MEM COMMAND
 5387 tty1     S      0:00     46   624  5147  1976  0.2 -bash
 5408 tty1     Sl     0:32    255   311 16872  4112  0.5 eggdrop /home/.../P25739 tty1     S+     0:00      9   624  5147  1796  0.2 -bash
25740 tty1     Rl+    0:29    173     1 218390 199604 25.7 mono --optimize=all S25792 pts/0    Ss     0:00      1   624  5015  3332  0.4 bash
25823 pts/0    R+     0:00      0    61  2134   864  0.1 ps -v

```

What this MAJFL means? a high number like 173 is (for mono) is because of my bad ram?

---

### Post by dcstar on 2006-04-03
[QUOTE=brodock]it's not a question about badram kernel patch but a failure ram module...

i know that one of my ram modules have problems (i did a memtest) but what i'm asking is about the command ps -v
i have an output like this:

```

  PID TTY      STAT   TIME  MAJFL   TRS   DRS   RSS %MEM COMMAND
 5387 tty1     S      0:00     46   624  5147  1976  0.2 -bash
 5408 tty1     Sl     0:32    255   311 16872  4112  0.5 eggdrop /home/.../P25739 tty1     S+     0:00      9   624  5147  1796  0.2 -bash
25740 tty1     Rl+    0:29    173     1 218390 199604 25.7 mono --optimize=all S25792 pts/0    Ss     0:00      1   624  5015  3332  0.4 bash
25823 pts/0    R+     0:00      0    61  2134   864  0.1 ps -v

```

What this MAJFL means? a high number like 173 is (for mono) is because of my bad ram?[/QUOTE]
MAJFL means the number of "Page Faults" a process has caused.

Page Faults are basically where the OS has to go to swap to move the desired virtual memory contents back into real RAM space for execution.

"Bad RAM" will crash your system and has nothing whatsoever to do with what you see in ps.

---

