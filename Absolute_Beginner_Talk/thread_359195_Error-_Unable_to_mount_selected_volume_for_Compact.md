---
title: "Error- Unable to mount selected volume for Compact Flash 2 card"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by CafeHarrar on 2007-02-11
Hello everyone!  After spend an unholy amount of money on the 2007 'student' edition of a certain office software suite, I got tremendously upset and have now completely freed myself from the vicelike grip of Redmond!  I have pretty much got everything setup well.  The problem, is that I have a Canon DSLR, with a 2gig Compact Flash card that I put into a little adapter dealey in my laptop... not quite sure what the dealey is called, but it works.  For whatever reason, Ubuntu detects it's presence correctly as EOS_DIGITAL, but when I try to open it I get: 

Unable to mount the selected volume 
error: device /dev/hda1 is not removable

error: could not execute pmount

First off, it is removable!!!  Aargh, I have to admit, using the terminal feels just like it did when I first learned msdos as a lad...  I did some searching, but could not find a solution.  Thanks everyone for putting up with a newbie's questions!

- Justin

---

### Post by taurus on 2007-02-11
Try

Applications -> Accessories -> Terminal
```
sudo mkdir /media/hda1
sudo mount -t vfat /dev/hda1 /media/hda1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by CafeHarrar on 2007-02-12
Thanks!  Seems to work now, I just have to put that line in whenever I put the card back in.

---

