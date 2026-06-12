---
title: "Dual Boot Help Please"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Killamurk07 on 2007-09-19
I have 2 HD's 1 with Ubuntu and Other with XP .. I was wonder how can I do a dual boot,? Oh yeah I don't even know what grub or grud is ...I am new to Linux and I am very dumb at Linux so I need help ..I am a windows baby...

---

### Post by oilchangeguy on 2007-09-19
read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
and haven't you already had a thread on dual booting? why are you starting another?
[http://ubuntuforums.org/showthread.php?t=549520](http://ubuntuforums.org/showthread.php?t=549520)

---

### Post by sailor2001 on 2007-09-19
from what I have read: with 2 hard drives, disconnect the one with windows and install ubuntu on the remaining one. Grub is the boot used by many os's. With the windows drive disconnected, it will still have mbr to boot windows, and wont be using grub

---

### Post by oilchangeguy on 2007-09-19
> **sailor2001 said:**
> from what I have read: with 2 hard drives, disconnect the one with windows and install ubuntu on the remaining one. Grub is the boot used by many os's. With the windows drive disconnected, it will still have mbr to boot windows, and wont be using grub

ok, please explain how the user can boot into windows with the hard drive disconnected? btw, i dual boot using two hard drives, so i'm really interested in your answer.

---

### Post by Killamurk07 on 2007-09-19
Umm I just decided to install Ubuntu on my Other hard drive I was wondering is there anyway to choose which HD to boot from...Any Help

---

### Post by oilchangeguy on 2007-09-19
> **Killamurk07 said:**
> Umm I just decided to install Ubuntu on my Other hard drive I was wondering is there anyway to choose which HD to boot from...Any Help

here's what i did. started with fresh install of windows, and ubuntu. installed windows on one hard drive (jumpers set to master). after it was installed i unplugged that hard drive. installed ubuntu on another hard drive (jumpers set to master). after it was installed, plugged in the windows drive (jumper set to slave). and grub picked up both operating systems, you have the option to choose either one.

---

### Post by Killamurk07 on 2007-09-19
> **oilchangeguy said:**
> here's what i did. started with fresh install of windows, and ubuntu. installed windows on one hard drive (jumpers set to master). after it was installed i unplugged that hard drive. installed ubuntu on another hard drive (jumpers set to master). after it was installed, plugged in the windows drive (jumper set to slave). and grub picked up both operating systems, you have the option to choose either one.

HUH what is grub? and how can I get to it?

---

### Post by oilchangeguy on 2007-09-19
> **Killamurk07 said:**
> HUH what is grub? and how can I get to it?

grub is short for grand unified boot loader. and it's included with ubuntu. also why are you interested in ubuntu? the more i read your posts, i'm thinking maybe you should stick with what you know. (windows)

---

### Post by Killamurk07 on 2007-09-19
I am interested in Ubuntu because my friend told me it is better then windows. and I am trying to get all the facts I want to know..But all I wanted to know was about the boot loader (grub) and how do I get the thing to load up so I can select my first HD with win XP when I find out that I will be satisfied..So I can load up any of my OS rather then unplugging the HD's

---

### Post by oilchangeguy on 2007-09-19
> **Killamurk07 said:**
> I am interested in Ubuntu because my friend told me it is better then windows. and I am trying to get all the facts I want to know..But all I wanted to know was about the boot loader (grub) and how do I get the thing to load up so I can select my first HD with win XP when I find out that I will be satisfied..So I can load up any of my OS rather then unplugging the HD's

did you not read post #6?

---

### Post by Killamurk07 on 2007-09-19
> **oilchangeguy said:**
> here's what i did. started with fresh install of windows, and ubuntu. installed windows on one hard drive (jumpers set to master). after it was installed i unplugged that hard drive. installed ubuntu on another hard drive (jumpers set to master). after it was installed, plugged in the windows drive (jumper set to slave). and grub picked up both operating systems, you have the option to choose either one.

OK I will do that...Thanks man for advice brb later

---

