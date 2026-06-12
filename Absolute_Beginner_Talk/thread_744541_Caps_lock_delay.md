---
title: "Caps lock delay"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by AdrianStrays on 2008-04-03
So this is a bit silly, but it is driving me CRAZY.  I don't type the proper way (I don't use shift) I use the Caps lock to capitalize letters. Something I immediately noticed when switching over to Ubuntu was that when ever I hit and then unhit caps lock there is a delay in processing it that is slightly longer than what is found in Windows.  So I start typing and get things like this:

TWas the night before CHristmas and all through the house
NOt a creature was sturring; not even the mouse
FOrget about CHristmas, just for one sec
THis silly caps lock problem, is like a kick in the dic....

Sorry, I'm not much a poet, but do you catch my drift?  Its very annoying when I am taking notes in class and then have to go back and fix the capitals...

---

### Post by Crafty Kisses on 2008-04-03
Weird, how much RAM do you have?

---

### Post by AdrianStrays on 2008-04-03
2 GB.  Thats the only key that does anything remotely like that.  I tried playing with the keyboard settings, but couldn't find a configuration that fixed it.  I don't have this problem in Vista, so it certainly isn't a hardware issue.

---

### Post by Crafty Kisses on 2008-04-03
> **AdrianStrays said:**
> 2 GB.  Thats the only key that does anything remotely like that.  I tried playing with the keyboard settings, but couldn't find a configuration that fixed it.  I don't have this problem in Vista, so it certainly isn't a hardware issue.

Hmmm, post the following output:
```
top
```
That's a really weird problem. :(

---

### Post by AdrianStrays on 2008-04-03
adrian@Alpha-60-Workstation:~$ top

top - 19:41:18 up  1:06,  2 users,  load average: 1.72, 1.57, 1.40
Tasks: 152 total,   1 running, 151 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.6%us,  1.7%sy,  0.0%ni, 90.7%id,  0.7%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1932664k total,   783252k used,  1149412k free,    23492k buffers
Swap:  1951856k total,        0k used,  1951856k free,   366096k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 6263 adrian    20   0  352m 127m  29m S    4  6.8  15:54.24 firefox-bin                                                                                     
 5800 adrian    20   0  297m 121m  14m S    3  6.4   7:13.82 Xgl                                                                                             
 5840 adrian    20   0 13684 8256 4464 S    1  0.4   0:26.02 compiz.real                                                                                     
 6385 adrian    20   0 86268  25m  16m S    1  1.4   0:02.53 pidgin                                                                                          
 6696 adrian    20   0  106m  22m  12m S    1  1.2   0:00.93 gnome-terminal                                                                                  
    6 root     -51  -5     0    0    0 S    0  0.0   0:23.28 softirq-timer/0                                                                                 
   19 root     -51  -5     0    0    0 S    0  0.0   0:24.54 softirq-timer/1                                                                                 
 2036 root     -51  -5     0    0    0 S    0  0.0   0:05.24 IRQ-16                                                                                          
 4981 klog      20   0  2628 1420  408 S    0  0.1   0:05.74 klogd                                                                                           
 5483 root      20   0 38316  10m 6520 S    0  0.6   0:15.59 Xorg                                                                                            
 5885 adrian    20   0 16644 3632 2692 S    0  0.2   0:04.45 gnome-screensav                                                                                 
 6719 adrian    20   0  2364 1188  876 R    0  0.1   0:00.18 top                                                                                             
    1 root      20   0  2948 1856  532 S    0  0.1   0:01.29 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      RT  -5     0    0    0 S    0  0.0   0:00.00 posix_cpu_timer                                                                                 
    5 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-high/0                                                                                  
    7 root     -51  -5     0    0    0 S    0  0.0   0:00.31 softirq-net-tx/                                                                                 
    8 root     -51  -5     0    0    0 S    0  0.0   0:00.06 softirq-net-rx/                                                                                 
    9 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-block/0                                                                                 
   10 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-tasklet                                                                                 
   11 root     -51  -5     0    0    0 S    0  0.0   0:00.60 softirq-sched/0                                                                                 
   12 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-hrtimer                                                                                 
   13 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-rcu/0                                                                                   
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
   15 root      10 -10     0    0    0 S    0  0.0   0:00.00 desched/0                                                                                       
   16 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
   17 root      RT  -5     0    0    0 S    0  0.0   0:00.00 posix_cpu_timer                                                                                 
   18 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-high/1                                                                                  
   20 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-net-tx/                                                                                 
   21 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-net-rx/                                                                                 
   22 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-block/1                                                                                 
   23 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-tasklet                                                                                 
   24 root     -51  -5     0    0    0 S    0  0.0   0:00.27 softirq-sched/1                                                                                 
   25 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-hrtimer                                                                                 
   26 root     -51  -5     0    0    0 S    0  0.0   0:00.11 softirq-rcu/1

---

### Post by Crafty Kisses on 2008-04-03
Have you tried different keyboards?

---

### Post by AdrianStrays on 2008-04-03
Its a laptop.

---

### Post by AdrianStrays on 2008-04-04
Bump

---

### Post by AdrianStrays on 2008-04-05
>:( Bump!

---

### Post by kbless7 on 2008-04-05
What is your caps lock preferences set to? Its under system>>preferences>>keyboard>>layout options

mine is set to default and i don't have this problem

---

### Post by AdrianStrays on 2008-04-05
Default

---

### Post by Kosimo on 2008-04-05
I can confirm this. It's been years since I felt it...  In windows the cap locks activation is much faster than in Linux. This is a fact believe me or not.

---

### Post by AdrianStrays on 2008-04-06
AH HA! I'm NOT crazy.  Come on.  There HAS to be a fix to this.  Its driving me nuts.

---

### Post by AdrianStrays on 2008-04-07
Come on....my documents are all capital ridden....

---

### Post by AdrianStrays on 2008-04-20
:(

---

