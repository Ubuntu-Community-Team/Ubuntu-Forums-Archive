---
title: "How do I tell how much memory is left"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by linuxuser28 on 2007-03-12
I'm checking my memory two different ways. First is with the terminal, I get this, which looks like I'm almost out of available memory.

            [LEFT]Mem:        [/LEFT]
    [LEFT]775424      total [/LEFT]
    [LEFT]754200      used[/LEFT]
    [LEFT]21224         free[/LEFT]
    [LEFT] 0       shared[/LEFT]
    [LEFT] 33420     buffers[/LEFT]
    [LEFT]588908   cached[/LEFT]
    [LEFT]-/+ buffers/cache:     131872     643552[/LEFT]
    [LEFT]Swap:      1510068          0    1510068

[/LEFT]
            [LEFT]However when I check the system monitor I get this, which looks like I have quite a bit left.

[/LEFT]
        [LEFT]130.7 MiB of 757.2 MiB  17.3%

[/LEFT]
        [LEFT]Which is the correct way to read this?[/LEFT]

---

### Post by [S|G] on 2007-03-12
> **linuxuser28 said:**
> I'm checking my memory two different ways. First is with the terminal, I get this, which looks like I'm almost out of available memory.

            [LEFT]Mem:        [/LEFT]
    [LEFT]775424      total [/LEFT]
    [LEFT]754200      used[/LEFT]
    [LEFT]21224         free[/LEFT]
    [LEFT] 0       shared[/LEFT]
    [LEFT] 33420     buffers[/LEFT]
    [LEFT]588908   cached[/LEFT]
    [LEFT]-/+ buffers/cache:     131872     643552[/LEFT]
    [LEFT]Swap:      1510068          0    1510068

[/LEFT]
            [LEFT]However when I check the system monitor I get this, which looks like I have quite a bit left.

[/LEFT]
        [LEFT]130.7 MiB of 757.2 MiB  17.3%

[/LEFT]
        [LEFT]Which is the correct way to read this?[/LEFT]

588908 cached - Not really used but reserved for system cache. Basically, keeping recent files in memory in case that if you access them the system won't need to fetch them again, making access faster. So the memory you're really using is 754200  -  588908 bytes

---

### Post by igknighted on 2007-03-12
Linux uses any free memory you have for caching to speed things up any way it can.  After all, unused memory is wasted memory.  If an application needs memory, however, it immediately get it and the caching that was being done there stops.  If you subtract the buffers and the cached from the total  memory used, you will find it is roughly the same as the other report.  Therefor, they are both correct, they are just telling you different things.  You have all your mem (minus 17.3%) available to your applications, but most of your memory is currently in use.

---

