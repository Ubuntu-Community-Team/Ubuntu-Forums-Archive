---
title: "[SOLVED] Partition too small"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by potatoehead64 on 2007-06-07
I installed Ubuntu 6 via the live update disk and everything went fine. It automatically created the required partitions to sit alongside Windows XP. I also successfully configured the modem drivers per the guide provided here. The problems came when I got on the net and downloaded updates. It used up the rest of the disk space and was unable to install required updates. Furthermore, I can no longer log in to Ubuntu because there is not even enough space to write a log file. 
Is there a way around this problem without having to use a partition manager (software that I don't have)?

---

### Post by durrell on 2007-06-07
Download this:

[www.sysresccd.org/](www.sysresccd.org/)

Burn it do a CD and then boot. You'll be able to use Gparted to repartition. How big is your hard drive?

---

### Post by dfreer on 2007-06-07
How big did you make your partition?

Can you log in via the Rescue kernel?

If not, you can run a live CD, and manually delete the files. Every package you download in ubuntu is saved to /var/cache/apt/archives/, you can clean this out and that should let you log in. But while you are in the live CD, you might as well give ubuntu some more space.

From the live CD, post the output of this command:
```
sudo fdisk -l
```
We'll try to see how much space you gave ubuntu, and try to move some things around so that you (hopefully) won't have to reinstall.

EDIT: You can use gparted from the Live CD, no need to download another cd and burn it :)

---

### Post by durrell on 2007-06-07
> **dfreer said:**
> 

EDIT: You can use gparted from the Live CD, no need to download another cd and burn it :)

Forgot about that..shows I'm still a total nub, haha.

---

### Post by dfreer on 2007-06-07
> **durrell said:**
> Forgot about that..shows I'm still a total nub, haha.

don't worry about it. just quicker to use a CD already burned then to download a new one and burn it :D

---

### Post by potatoehead64 on 2007-06-08
Thanks folks. I've got it sorted now. Although I think I have more partions on my 80gig hard drive than I need!!! LOL. I'm up and running now with about a couple of gig spare on the partition where Ubuntu is. 
I've loads to learn here. Trtying to get round some of the terminal commands needed.

---

