---
title: "Disk Manager- Why don't I have it?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by JacobRogers on 2007-04-30
First off, I don't know what version of Ubuntu I have.  I know I've had it on my laptop for quite some time now, so maybe Disks Manager isn't on this version. [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html)

That help files talks about mounting a hard drive with that Disks Manager utility.  As it stands I can't access my Windows partition while I'm in Ubuntu and I'd really like to.  Any help?

Jak

---

### Post by blackened on 2007-04-30
What filesystem are you using on the Windows partition? fat32, or ntfs?

---

### Post by JacobRogers on 2007-04-30
ntfs, thanks for replying

---

### Post by zvacet on 2007-04-30
**system>about ubuntu** will tell you wich version you are runing or you can do this

```
lsb_release -a

```

I don´t think that app is still available.

---

### Post by JacobRogers on 2007-04-30
Alright, I have 6.10.  Neat.  When you say, "I don't think that app is still available" are you talking about Disks Manager?

---

### Post by JacobRogers on 2007-04-30
I think I'm gonna try to update to the 7.whatever version sometime after finals!  I can't risk messing up my computer right now though!

---

### Post by JacobRogers on 2007-05-01
After updating to the new version, it automatically recognized both of my window partitions.  I just need to remember not to right on them, right?  Because that's risky?

Is that right?

---

### Post by blackened on 2007-05-01
I'm pretty sure most of the issues with writing to ntfs have been resolved. Granted I'm no expert and you should research it a bit more, but I've not had any problems with it personally.

---

