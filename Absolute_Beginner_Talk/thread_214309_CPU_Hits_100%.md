---
title: "CPU Hits 100%"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Hexx on 2006-07-12
I have a problem with some programs making my CPU usage jump to a constant 100%.

When I load up the zSNES emulator, CPU usage jumps to 100%, just being open, no ROMs loaded.

Also, when I try playing movies in VLC, CPU usage hits a constant 100%.

It seems when running things in Ubuntu, my CPU usage can be quite high. I don't have this problem with Windows.

Does anyone else have problems like this? Is there a way to fix this?

---

### Post by Teroedni on 2006-07-12
Depends
first of all how powerfull is your cpu

1.Open A terminal and paste ```
cat /proc/cpu
```

You will get an answer past it here

2.Open Terminal again
paste this code into it
```
uname -a
```

Again you will get an Answer paste it here

---

### Post by mrcl on 2006-07-12
Open a terminal and use the command top, then you will be able to see what program is using all you cpu time, and if is them same program for both cases. Knowing that is easier fix the problem!!!

---

### Post by Hexx on 2006-07-12
> **Teroedni said:**
> Depends
first of all how powerfull is your cpu

1.Open A terminal and paste ```
cat /proc/cpu
```

You will get an answer past it here

2.Open Terminal again
paste this code into it
```
uname -a
```

Again you will get an Answer paste it here

The first command you gave tells me there's no such file or directory... :/

The second command gives me this: ```
Linux Hexxennwerks 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
```

I'm running on an old 500 MHz Intel Celeron processor though. Is this not enough to run Ubuntu? I have Windows XP Pro running pretty damn snappy, including zSNES and VLC on Windows. I don't get these CPU usage problems using these programs on Windows, so I'm baffled.

Thanks for your help.

---

### Post by Teroedni on 2006-07-12
Well a 500mhz Celelron isent the strongest you could run Ubuntu on
But i see your running the i386 kernel
I would advise you to change to the 686 kernel as thjat kernels contains optimizations for pentium proc.
That may be the thing you need to get the performance up to par with the Xp.


AS for the command i did a error
It should have been
```
cat /proc/cpuinfo
```
Sorry for that

---

### Post by Hexx on 2006-07-12
> **Teroedni said:**
> Well a 500mhz Celelron isent the strongest you could run Ubuntu on
But i see your running the i386 kernel
I would advise you to change to the 686 kernel as thjat kernels contains optimizations for pentium proc.
That may be the thing you need to get the performance up to par with the Xp.


AS for the command i did a error
It should have been
```
cat /proc/cpuinfo
```
Sorry for that

Yeah 500 MHz is quite pathetic, but I have WinXP running rather nicely so I figured there must be some way that I could get Ubuntu to run much the same.

I'll change my kernel as you suggested. Is there anything I should know about doing this?

---

### Post by NT4usB on 2006-07-12
> **Hexx said:**
> ...
I'll change my kernel as you suggested. Is there anything I should know about doing this?

[http://www.ubuntuforums.org/showthread.php?t=213420](http://www.ubuntuforums.org/showthread.php?t=213420)

---

### Post by Metacarpal on 2006-07-12
I changed to the 686 kernel as a complete newbie and was scared snotless... but don't be.  It's as easy as opening synaptic, searching for 686, and clicking a few boxes.

...but I'll let one of the pros here give the specifics on that.  Just wanted to tell you it's painless.  :D

---

### Post by cyberlion on 2007-01-28
I have the same problem posted by the first post... when I load any rom in zsnes the CPU usage go to 100%.
Any sugestion?!

---

### Post by codypumper on 2007-01-28
Run "top" in terminal please

---

### Post by cyberlion on 2007-01-29
Ok... without zsnes:
```

top - 07:57:48 up 28 min,  4 users,  load average: 0.92, 0.53, 0.51
Tasks:  86 total,   1 running,  85 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.3% us,  0.3% sy,  0.0% ni, 96.0% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:    352992k total,   289324k used,    63668k free,     4996k buffers
Swap:   811240k total,    18388k used,   792852k free,   134012k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4591 root      15   0  134m  17m 7356 S  2.3  5.0   2:54.56 Xorg
 5218 rodrigo   15   0 45204  14m 9312 S  0.3  4.3   0:04.71 gnome-terminal
 9729 rodrigo   16   0  2200 1100  856 R  0.3  0.3   0:00.13 top
    1 root      16   0  1568  532  460 S  0.0  0.2   0:01.18 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0
   10 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  126 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  127 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  129 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  128 root      15   0     0    0    0 S  0.0  0.0   0:00.15 kswapd0
  717 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
```

Zsnes is run:
```

top - 07:59:22 up 30 min,  3 users,  load aver
Tasks:  86 total,   2 running,  84 sleeping,
Cpu(s): 97.3% us,  2.7% sy,  0.0% ni,  0.0% id
Mem:    352992k total,   301260k used,    5173
Swap:   811240k total,    18388k used,   79285

  PID USER      PR  NI  VIRT  RES  SHR S %CPU
 4591 root      25   0  134m  17m 8252 R 70.1
 9799 rodrigo   16   0 54908  15m 3692 S 27.9
 5020 rodrigo   15   0  8740 3888 3064 S  0.3
 5133 rodrigo   16   0 14776 2776 1852 S  0.3
    1 root      16   0  1568  532  460 S  0.0
    2 root      RT   0     0    0    0 S  0.0
    3 root      34  19     0    0    0 S  0.0
    4 root      RT   0     0    0    0 S  0.0
    5 root      10  -5     0    0    0 S  0.0
    6 root      10  -5     0    0    0 S  0.0
    7 root      10  -5     0    0    0 S  0.0
    9 root      10  -5     0    0    0 S  0.0
   10 root      10  -5     0    0    0 S  0.0
  126 root      15   0     0    0    0 S  0.0
  127 root      15   0     0    0    0 S  0.0
  129 root      11  -5     0    0    0 S  0.0
  128 root      15   0     0    0    0 S  0.0
  717 root      10  -5     0    0    0 S  0.0
```

---

### Post by cyberlion on 2007-01-29
I reinstaled the dbus and now the zsnes work in 40 to 50%...

	
it remains to see if it continues restarting the system.

---

