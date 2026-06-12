---
title: "Gparted Help"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by HdK on 2007-03-10
When I run gparted , there is a lock next to /dev/sda1 , I am trying to resize it to install vista Why is the lock there not letting me resize the partition

---

### Post by Bachstelze on 2007-03-10
Are you running GParted from a Live CD or from your installed Ubuntu ?

---

### Post by HdK on 2007-03-10
installed ubuntu

---

### Post by etank on 2007-03-10
Try using the Live CD from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). I think that it may be a newer version.

---

### Post by HdK on 2007-03-10
i installed gparted using the synaptic package manager

---

### Post by Bachstelze on 2007-03-10
You cannot resize a partition while it is in use. Use a Live CD.

---

### Post by rusty4r on 2007-03-10
Is this partition the one your working in? or maybe the one listed as the boot partition?

either way the live cd of gparted will not have that problem, or you could use the system rescue cd or I think even the livecd that you installed from may be able to do it for you

---

### Post by HdK on 2007-03-10
This still does not answer how to get the locked drive unlocked to resize it

---

### Post by rusty4r on 2007-03-10
what everyone is trying to say is that if you use the livecd it won't be locked

---

### Post by luke411 on 2007-03-10
If you boot from the cd, you are not booting from  your hard drive, thus the hard drive partitions will not be in use and therefor, will not be locked and you should be able to resize it. You cannot resize a partition that is currently running. So, use the live cd.

---

### Post by houstonbofh on 2007-03-10
> **HdK said:**
> This still does not answer how to get the locked drive unlocked to resize it
Yes it did.  If the drive is mounted, it is locked.  If you boot from the gpartd live cd, it will not be mounted.  If you boot from your hard drive, it will.

---

### Post by HereInOz on 2007-03-10
In plain speak:

The reason that the drive is locked is because it is the one that you are using when you are running Ubuntu.  You cannot resize a partition that is currently being used by your operating system.

Hence you need to stop using that drive so that you can resize it.  How do you do that?

Get hold of a Live CD, or download the iso to make a bootable GParted CD, boot the computer from that, and you will see that the drive that was locked is now not locked, and you will be able to re-size it.

What you have been trying to do is like trying to change the engine in a car, while still using the car.  Just isn't going to work.

---

### Post by dhughes on 2007-03-10
> **HdK said:**
> This still does not answer how to get the locked drive unlocked to resize it

 HymnToLife was right...

 [quote=HymnToLife] You cannot resize a partition while it is in use. Use a Live CD.[/quote]

 You can't resize a partition that is in use in other words "mounted". The lock may be Gparted's way of telling you the partition you're trying to resize is in use, if it's not in use  you may not have any room to resize it.

 I know I had Windows on hda1, Ubuntu was on hda3, hda2 was not used, hda5 (really hda4) was Swap. I wanted to resize hda2 to put Ubuntu on that instead of hda3 but since hda2 came before hda3 I couldn't.

 Anyway, try making a LiveCD of Gparted, boot from it and then see if the locked symbol is there. If it isn't then it was probably because the drive and partitions were in use and couldn't be altered.

 The fact Gparted is available on a running system is either a mistake or it's possible you can unmount a partition (except hda1, or whatever Ubuntu is on of course) and then resize it but then of course you could only shrink it since you won't be able to touch the other partitions that are in use.

 To make a long story short: Booting from the LiveCD would be much easier!

** edit:** I just looked at Gparted and I see what you're talking about, the lock icon is to the right of the partition name e.g. /dev/hda1    X <--lock symbol . You can right click the partition and choose "unmount", if that is not possible then you get a warning saying so.

---

### Post by Patrick K on 2007-03-10
The lock means the partition is mounted. You cannot perform any operations on a mounted partition. With GParted installed, several partitions will remain unavailable for operations since they are in use. Others, that are not in use, can be unmounted (unlocked) and you can perform operations on them. If you right click on the partition, there is an option to unmount the partition. When you boot from the LiveCD all partitions are unmounted. That is why the other are saying to use the LiveCD.

---

### Post by tvor on 2007-04-06
I have exactly the same problem, it puzzles me, why it the Gparted in Ubuntu at all if (as it sounds like) you can't use it on any partitions in use!

Is it there for external HD or Windows partitions? :confused:

---

### Post by Bachstelze on 2007-04-06
Of course you can't ! Resizing a partition while it is in use is a crazy thing to do so it won't let you do it. It is there for anything that doesn't involve currently mounted partitions.

---

