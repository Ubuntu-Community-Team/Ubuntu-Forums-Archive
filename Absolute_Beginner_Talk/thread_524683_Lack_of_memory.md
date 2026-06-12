---
title: "Lack of memory"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by umiki on 2007-08-13
Hello all..

I am newbie in linux and ubuntu. I like it a lot, but there is annoying problem.

I have a workstation with 2.0 GHz CPU and 1,3 Gb of RAM.
When I installed Ubuntu I have 256 MB of RAM.

I have a problem that ubuntu freezes. completly. only reset computer helps.
Because of that I bought additional RAM but no progress. :(

Here is my log of free -m command within 10 minutes, After I startup computer, I set download 1 gnome-btdownload, set another gnome-btdownload. After I quit 1 btdownlad, nothing changes. I am also wonder how that ubuntu does not show any message about lack of memory just freeze.

Should I resize swap?

I would be very happy if you could help me to solve this problem, because it is very irritating.

here is log of my memory:

haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265        274        991          0          6        160
-/+ buffers/cache:        108       1157
Swap:          729          0        729
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265        306        958          0          6        178
-/+ buffers/cache:        121       1144
Swap:          729          0        729
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265        306        959          0          6        178
-/+ buffers/cache:        121       1144
Swap:          729          0        729
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265        309        956          0          6        179
-/+ buffers/cache:        123       1142
Swap:          729          0        729
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265        312        953          0          6        179
-/+ buffers/cache:        125       1140
Swap:          729          0        729
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265        525        740          0          7        377
-/+ buffers/cache:        139       1126
Swap:          729          0        729
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265       1141        124          0          9        979
-/+ buffers/cache:        152       1113
Swap:          729          0        729
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265       1245         20          0          1       1066
-/+ buffers/cache:        177       1088
Swap:          729         18        711
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265       1245         19          0          3       1080
-/+ buffers/cache:        162       1103
Swap:          729         18        711
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265       1241         23          0          1       1080
-/+ buffers/cache:        159       1106
Swap:          729         18        710
haris@MASTER:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1265       1242         23          0          2       1078
-/+ buffers/cache:        161       1104
Swap:          729         18        710
haris@MASTER:~$

Bye!

---

### Post by nvrpunk on 2007-08-13
Pull out the 256 Meg stick, just use the 1Gb.  Reboot.

Hopefully that helps. 

It isnt a software problem.

---

### Post by umiki on 2007-08-14
I have removed 256 MB stick. Now I have 2x512 mb sticks.
For sometimes it looks good, but today in the morning comp again freeze :(

There is something strange to.
When I check free-m it shows me that I got only 24 free memory.
If I check system monitor I got I use only 10% 
Any idea????

Where and how to check which process has responsible for freezing.

any other idea how to solve this problem.

Thanks.

---

### Post by ramjet_1953 on 2007-08-14
Quite often, lockups are associated with video card issues.

What video card / chipset do you have?

How much RAM does the card have /or how much shared memory is allocated to the chipset?

Have you loaded a propriatory, or open source driver for your video?

Regards,
Roger :cool:

---

