---
title: "partition scares me, heelp!"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by flavio newbie on 2007-03-11
Hello guys, im trying to do a partition of an external hard disk, but after i unmount it the only option i get is format.. how do i do a apartition without losing the data? i have 35 gb that i don't know where to put..
help im really bad with computers..

---

### Post by mikewhatever on 2007-03-11
You can only create a partition in the unallocated space. Assuming you external HDD has non, you'll need to resize the existing partition, thus creating unallocated space where you can create more partition. Before you go ahead resizing, it is strongly advisable to defragment that partition.

---

### Post by flavio newbie on 2007-03-11
and how do i resize? sorry i ask about everything
thanks

---

### Post by guysmiley25 on 2007-03-11
I've heard that ubuntu auto mounts external devices with I expect is causing your problem. I use xubuntu witch does not do this.

```
sudo umount /media/usbdevice
```

where /media/usbdevice is the path to where your external hard drive is mounted. 

Run this command a few times until you get a reply that says something about it not being mounted.

The open up gparted and resize your partition. Make a new one or whatever.

Also what could be causing your problem is if ubuntu is installed and running of that drive? Is this the case? If so you will have to boot to the live CD to do the operation.

I have not personally resized a partition with gparted before and I'm not 100 percent on whether it saves your data or not. It always pays to back up before doing such an operation.

---

### Post by flavio newbie on 2007-03-11
its an external hardisk, but on gparted i cant find the optio resize...

---

### Post by guysmiley25 on 2007-03-12
I'm sure the only reason that could be so is if the drive is mounted! Other wise I have no idea. I've just tried it now.

Another program you could try witch is a DOS program is pqmagic. That's what I used to use before I discovered the wonderful world of Linux.

One more thing you could try is try doing the operation from the Live CD.

---

### Post by indytim on 2007-03-12
If you are running GParted, you can "right mouse click" on the desired partiton. You will see a "Unmount" option.  

IndyTim

---

