---
title: "What did i just do?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2007-01-08
Hello!

I have just booted into linux, where it proceeded to force a check of the drive. (dunno why)
It found this
```

Illegal block #(NumberHere) In Inode
```that was 21 lines of that, each exactly the same except #(numberhere) had numbers 1-21
I then had to do a manual fsck(sp?) in root, Where it did this
```
multiply claimed blocks in inode
```Followed by lines, upon lines of numbers.

Care to tell me what i just did? Cause i certainly don't know!

---

### Post by kebes on 2007-01-08
Basically during bootup Linux detected some hard disk errors. The "fsck" command stands for "filesystem check" and it will repair hard disk errors. If you don't get the errors during boot anymore, then everything is fine. If you keep getting errors like that, it means that your hard drive is slowly failing (you may want to replace it before you start losing data!).

You will usually also get those errors if you turn off the computer without going "shutdown" (like if there's a power failure or whatever), since the disk is left in an "inconsistent state" and must be repaired.

---

### Post by Captain Kirk76 on 2007-01-09
it did it again, this time this happened.


Upon start of Linux, it forced another check.
It found this
```
Inode (number) was part of an orphaned Inode List
```
There was 4 lines, and 4 differend erros of the same type of that.
It also found...
```
Inode (number) ref count is 12, should be 13
```
```
Inode (number) ref count is 8, should be 10
```

---

### Post by johnnymac on 2007-01-09
Sounds like your disk is going...is this a SATA disk and how long have you had it?

---

### Post by kebes on 2007-01-09
Back up any important data from that disk ASAP.

Then use/reboot the computer a few times. If new errors always appear, try reformatting the whole thing. (During a format the disk may be able to identify bad sectors and quarantine them.) If the format returns errors (or the disk starts dying again after format), then you probably need a new drive. Check your warranty.

Remember: your data is the most important thing. New hard drives are cheap. Your data isn't.

---

### Post by P235 on 2007-03-10
Hi, I'm using an [HP Pavilion N5495]("http://www.if.pw.edu.pl/~kisiel/laptop/hplinux.html") and I am experiencing the same problems as Kirk here.  I've had this laptop for years now and I'm pretty sure my hard drive is IDE because the partition labels are hda1, hda2, hda3...etc.  My hard drive model is HITACHI_DK23CA-30 ATA DISK, if that helps.  How much time do I have left with my hard drive?

---

### Post by johnnymac on 2007-03-10
It is very hard to say.  In most cases, things will seem "okay" but one day you'll go to boot and it just won't.  So - back up anything you have that's important and look into another hard-drive.

---

