---
title: "what slows down ubuntu?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by JewelledDragon13 on 2008-04-14
My Feisty Fawn normally runs well, but has been slowing down lately, taking a long time to open things and so on.  I don't have a good sense of what sorts of things make Ubuntu slow down like I do with Windows.  

Where should I be looking to figure out what's slowing me down?  What (software wise) are some fixes?

Specs:
P4 3.2 GHz
1 G ram
30 G hard drive but mostly empty
GeForce 6800

---

### Post by Seisen on 2008-04-14
Open up "top" in the terminal and post what it says  here.

---

### Post by Martje_001 on 2008-04-14
You can do a fsck on your hard disk by booting up a live cd and doing:
```
fsck /dev/sdx
```

Also, you can look in System --> Administration --> Services.

And last but not least, there is a tool which logs the startup time of all programs on bootup. I forgot it's name unfortunately..

---

### Post by y6FgBn)~v on 2008-04-14
Were you thinking of BUM Martje?

---

### Post by stchman on 2008-04-14
> **JewelledDragon13 said:**
> My Feisty Fawn normally runs well, but has been slowing down lately, taking a long time to open things and so on.  I don't have a good sense of what sorts of things make Ubuntu slow down like I do with Windows.  

Where should I be looking to figure out what's slowing me down?  What (software wise) are some fixes?

Specs:
P4 3.2 GHz
1 G ram
30 G hard drive but mostly empty
GeForce 6800

If you have lots of programs booting up in the Sessions Manager for your profile then it can slo things down.

---

### Post by JewelledDragon13 on 2008-04-14
Top says (I have Amarok and Firefox running):

top - 16:37:49 up  5:37,  2 users,  load average: 0.11, 0.14, 0.16
Tasks: 143 total,   1 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.1%us,  0.2%sy,  0.0%ni, 97.2%id,  0.0%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   1034644k total,   994616k used,    40028k free,   169984k buffers
Swap:  1108412k total,      204k used,  1108208k free,   462004k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5762 root      15   0 61352  47m   9m S    2  4.7   2:12.39 Xorg               
 6351 katz      15   0 44176  13m 8784 S    1  1.3   0:21.39 metacity           
 9099 katz      15   0  148m  52m  28m S    1  5.2   3:42.88 amarokapp          
 8920 katz      15   0  245m  87m  28m S    0  8.6   4:24.22 firefox-bin        
 6360 katz      15   0 83448  28m  19m S    0  2.8   0:12.72 nautilus           
 6416 katz      15   0 65292  10m 8588 S    0  1.1   0:00.11 trashapplet        
    1 root      18   0  2912 1848  524 S    0  0.2   0:01.26 init               
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    8 root      10  -5     0    0    0 S    0  0.0   0:00.15 events/0           
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   10 root      18  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread

---

### Post by Martje_001 on 2008-04-15
> **pcybill said:**
> Were you thinking of BUM Martje?
I meant bootchart :)

[http://ubuntuforums.org/attachment.php?attachmentid=14696&d=1156272463](http://ubuntuforums.org/attachment.php?attachmentid=14696&d=1156272463)

---

