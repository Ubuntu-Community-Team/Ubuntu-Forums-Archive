---
title: "RAM problems"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by boyturtle on 2007-11-05
I have 4 RAM slots and have been using 2 x 512 mb until now quote happily. I need more RAM for running VMWare and have bought 2 x 1 Gb giving me a total of 3 Gb.

Had problems with the first lot of ram with errors in memtest and got replacements. They tested fine and all 3 gb ran fine it the xp boot (WITH NO ISSUES AT ALL). When I boot to Ubuntu it hangs after a short period of time. If all 4 slots filled this problem persists. The problem goes away if I only use slots 1 and 2 (I have to use bridged memory, 2 slots. on my mobo). So for Ubuntu to work, I can run it on a max of 2gb with the other 1 gb removed:mad:

The same thing happens when I boot into the live cd

The memory is all correct, its the same spec as before from Kingston, only bigger

Any ideas anyone?

---

### Post by jaybombalous on 2007-11-05
are those dual channel slots? How are u running them in the bios?

---

### Post by milton1 on 2007-11-05
do all 3 GB show in POST?

When you run ubuntu with all 3 GB, what do you show from ```
free -m
```

how big is your swap partition?

---

### Post by boyturtle on 2007-11-05
It is my understanding that they are dual channel, as they have to be used in pairs and one stick of memory by itself will not work. Not sure I understand what you mean by 'How are u running them in the bios?' No adjustments to the ramcan be made in my bios. 

All 3 Gb show in post. Swap file is 3 gb and free -m gets the following
>              total       used       free     shared    buffers     cached
Mem:          3024        473       2551          0          8        222
-/+ buffers/cache:        241       2782
Swap:         2863          0       2863

---

