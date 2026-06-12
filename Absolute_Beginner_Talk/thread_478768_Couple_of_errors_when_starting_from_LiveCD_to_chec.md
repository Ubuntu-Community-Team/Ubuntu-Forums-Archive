---
title: "Couple of errors when starting from LiveCD to check Ubuntu"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Cristatus on 2007-06-19
I had the following errors happen to me:

[  249.714668] buffer i/o error on device fd0, logical block 0
[  287.928040] buffer i/o error on device fd0, logical block 0

I am a complete newbie to this, but from what it seems, fd stands for floppy disk, right?
That  doesn't make sense because I started the LiveCD, not a LiveFloppy ;)

Anyways, I also got a couple of other errors, and I have no idea how to look at them, but I couldn't get the time to write down what the errors were.

Thanks in advance.

---

### Post by Happy_Man on 2007-06-19
Do they prevent you from booting? If so, we'll need those other errors, because those shouldn't do much (heck, I get like five of those myself every time I boot, and I'm ok!).

Also, a bit of an explanation as to why booting a CD involves floppy drives: When the liveCD boots, it detects and mounts (means recognizes they exist) every external and internal drive on the computer (with the exception of the CD drive it's booting from, duh). Because, a LIveCD is meant to emulate a true desktop install as much as possible, and a desktop wouldn't be very much if you couldn't insert a floppy. So, the LiveCD mounts them.

---

### Post by Cristatus on 2007-06-20
Ok. That makes a lot of sense. It does not prevent me from booting into Ubuntu though.

So I was correct in assuming that those errors were for the floppy disk, right? There for it shouldn't have any problem for me running Ubuntu as normal.

I think I will go ahead and install Ubuntu tonight, as long as I can get my data of my other HDD.

Anyways, thanks for the help.

---

### Post by Happy_Man on 2007-06-20
No problem. Just, before installing, check the floppy drive. Just in case.

---

### Post by Cristatus on 2007-06-26
A bit late, but I checked  and went ahead with the installation, it seems to be ok, except for the fact that there is no internet on the box, but that's for another thread.

---

