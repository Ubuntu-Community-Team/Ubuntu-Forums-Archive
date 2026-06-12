---
title: "CD Drive wont open"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by MattVonFat on 2005-09-17
I've just started with Linux and i'm having problems witht he CD drive. The only time i can open and close it is as soon as i start up the computer. While its running the OS i can't do a thing with the drive. I've tried ejecting it through the right click menu but it says something about unmounting being busy? (i'm not sure what unmounting is either). Can anyone help?

---

### Post by blastus on 2005-09-17
Mounting means that Linux is prepared to read from or write to the given filesystem. MS-Windows also mounts filesystems but it is done automatically so you won't hear the term "mounting" too often in MS-Windows but it's there. A lot of Linux distributions do not automatically mount/unmount filesystems but it is easy to setup them up to do so. The advantage of this approach is that Linux gives you more control over what to mount and what not to mount and where to mount something. 

If the CD device is busy, it is mounted and the eject button on the drive won't work. To eject it, it must first be unmounted. I don't have Ubuntu installed right now, but if you right-click on the CD drive on the desktop there should be an option to unmount it.  :)

---

### Post by davmac on 2005-09-17
What happens when you open up a terminal window and type "sudo eject /media/cdrom"?

Dave Mac

---

