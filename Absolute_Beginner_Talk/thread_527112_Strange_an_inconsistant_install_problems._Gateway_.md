---
title: "Strange an inconsistant install problems. Gateway Laptp"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-08-16
Ok, so I just got a laptop, first thing I wanted to do was put Linux on it. So I popped in my Ubuntu 7.04 CD that i had ALREADY USED, and booted it up, about half way through the boot, I got a bunch of errors that were something like this:
```

tty1
tty2
tty3
tty4
tty5
tty6
tty7
```
Then it would start over again at 1, it looped about 3 or 4 times.
Strange I thought, but the boot continued, it got all the way to the xserver boot, where it failed, saying it couldn't start a proper xsession, and I was left with a brown screen and the terminal. 
So I thought, that's weird, and I turned of the computer, cleaned off the CD, and started it again. This time it booted perfectly fine, so I started the install. It went perfectly fine till about 60% or so, where it just canceled itself. It just stopped. No error message or anything. Just close out, and then the whole live CD froze.
I tried it again. Same results.
So then I downloaded the alternate install disk and burned it, everything went fine till it got to the kernel install, and it said it failed. So I started it again, this time selecting a different kernel version. Same results.
Then I downloaded ANOTHER live CD for 7.04. and I got the exact same results as the first. Around 60% it just stopped installing. No error message.

So my question is this: What the crap is happening and why are the disks all failing, seemingly at the same point?

---

### Post by Inxsible on 2007-08-16
Suspected problems

1) Graphics Card (Isnt it always :rolleyes:)
2) Memory
3) Processor Speed

---

### Post by Hobo Joe on 2007-08-16
Update: Tried it twice with the most recent disk, first time it returned an error that it couldn't copy files to the hard drive. The first time it was a python file, the second time it was some different file, something that I wasn't familiar with.

> **Inxsible said:**
> Suspected problems

1) Graphics Card (Isnt it always :rolleyes:)
2) Memory
3) Processor Speed

I don't think it's the graphics card, considering that the alternate install CD still messed up. 
Memory is the most likely, I'm checking it right now.
Processor speed is possible, but I don't think it's likely.

---

### Post by oilchangeguy on 2007-08-16
please advise your computers specs.

---

### Post by Hobo Joe on 2007-08-16
> **oilchangeguy said:**
> please advise your computers specs.

It's running a memtest right  now, so I'll go my best from memory:

Intel centrino, 1.86 Gh
Intel 915GM/GMS express mobile.
1GB of memory
I'll try and post better specs once the memtest is done.


Also, I think I should mention the suspicion that the harddrive may be faulty, due to the fact that it kept returning errors about things not be able to write to disk.

---

### Post by Hobo Joe on 2007-08-16
I'm pretty sure it's the hard drive now, but I"m still not positive, I keep getting erros with writting to the hard drive. 

Then I tried messing with the partition but when ever I tried to edit the partition would mount itself and the changes wouldn't work, even when I unmounted. However, I was able to make changes with the gparted live disk, so that mey not be it.

I'm really stumped here.....

---

