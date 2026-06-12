---
title: "Dual boot?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2007-01-17
Alright, I have been happily using ubuntu for some time now. 

But i have a need for windows for work related applications and a game or two.

So i would like to go the dual boot route.

My question:  Can I create a duel boot without wiping the contents of my hard drive?

 I have a massive media collection going which i would rather not have to back up at the moment. (im talking about 100gb)

So is there a way to take a partition of the free space i have and create a dual boot system?

---

### Post by Spr0k3t on 2007-01-17
Please bear with me, I'm very new to Linux using in general, but I believe there is a way to do this.

Use gparted to partition the free space on your hard drive

sudo aptitude install gparted

Then install your choice of OS on the free partition.  You will then need to modify the boot order, but I haven't figured out that part yet.  I'm new, so cut me some slack, but I know this much at least.

---

### Post by bodhi.zazen on 2007-01-17
You can resize an existing partition and install windows.

[list=number]Resize from a live CD, either the Ubuntu Desktop or Gparted (live CD)
[*]Watch that the partition number of your ubuntu root and swap do not change, otherwiase you will need to edit fstab.
[*]Windows MUST be installed to a PRIMARY partition.
[*]After installing windows you will need to re-install grub.[/list]

Re-install grub: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

GParted:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

HTH 8)

---

### Post by jvc26 on 2007-01-17
> **Spr0k3t said:**
> Please bear with me, I'm very new to Linux using in general, but I believe there is a way to do this.

Use gparted to partition the free space on your hard drive

sudo aptitude install gparted

Then install your choice of OS on the free partition.  You will then need to modify the boot order, but I haven't figured out that part yet.  I'm new, so cut me some slack, but I know this much at least.

It might be a better plan as Bodhi was mentioning to use the Gparted live cd - this is because then the drive isnt mounted when you are formatting it - something which can cause one hell of a lot of problems, and I'm pretty sure is impossible to do! By using the live cd all the changes should be able to be made :)

Il

---

### Post by Spr0k3t on 2007-01-17
Excellent suggestion Illuvator... that one is going in my journals.

---

