---
title: "Ubuntu: slow after hard disk resized, including VirtualBox"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-03-16
Since I am out of space, I decided to resize my Ubuntu Partition. I have more than 5GB of space now.

Weird, some things are not right with Ubuntu. Like opening a folder takes a few seconds longer than before, that is before I resize my Ubuntu partition to gain space. [http://ubuntuforums.org/showthread.php?t=724073](http://ubuntuforums.org/showthread.php?t=724073)

What more weird is that VirtualBox, since I have installed Windows XP there, it runs so slow!

And it makes my mouse lag, then Ubuntu hangs! I have to restart it manually or turn off my computer manually!

I never experienced any hangs in VirtualBox before resizing my hard drive.

When starting Windows XP over VirtualBox, Ubuntu lags. After booting with XP (the taskbar appears), everything is OK although Ubuntu responds slower as If VirtualBox is taking all the memory but it's not, before the resizing I think, this does not happens, Everything is fast.

While XP is running over VirtualBox, when I am opening folders in Ubuntu, it really takes time and slow. Is it because I set the folders to be accessed in XP via VirtualBox Guest Additions? Well, IT NEVER happened to me before. Before, I can access everything fast! Even XP is running via VirtualBox.

What happened guys? Or do you think, ah, the virtual hard drive in VirtualBox is placed on some partition in my hard drive and is corrupted? Do you think I have to delete everything and install XP again?

So, if that is the case, I always have delete everything in VirtualBox everytime I resize my hard drive?

click the image below to enlarge:

[[IMG]http://www.imageox.com/graphic/thumbs/201014-Screenshot-th.png[/IMG]](http://www.imageox.com/share/201014-Screenshot.png)

---

### Post by Fixman on 2008-03-16
Do you have a swap partition? To know, just install gparted and open it, then screenshot and post the results.

---

### Post by karlo on 2008-03-16
> **Fixman said:**
> Do you have a swap partition? To know, just install gparted and open it, then screenshot and post the results.

OK, I have to SWAP, which is weird. I have to change the UUID on the fstab file again.

Why does this always happen? Why does Ubuntu, does not automatically change the UUID of the SWAP?

How will I get the UUID again?

---

