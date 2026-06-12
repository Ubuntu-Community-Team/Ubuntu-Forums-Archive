---
title: "two OS"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-15
is it possible to have window and ubuntu on the same computer becuase when you install one it seems to erase the other.

---

### Post by talsemgeest on 2008-03-15
Yes you can. The easiest way to do this is when you are installing ubuntu, make sure you tell the installer to resize the partition with windows on it. After the installation, you will have both windows and ubuntu on the same computer, with the choice to start one or the other whenever you want.

Hope this helps :)

---

### Post by zvacet on 2008-03-15
Read [this.](http://www.psychocats.net/ubuntu/installing)

---

### Post by herbster on 2008-03-15
Just to expand on talsemgeest's post, you'd be resizing a Windows partition in the event that you have one single partition. You'd be "splitting" your hard drive into two so that one part has Windows and the other has linux. Just ensuring you're crystal clear so you don't lose data as a result or anything.

---

### Post by Sef on 2008-03-15
Here's a tutorial on [dual booting]("http://www.psychocats.net/ubuntu/installing") by Psychocats.

---

### Post by talsemgeest on 2008-03-15
> **herbster said:**
> Just to expand on talsemgeest's post, you'd be resizing a Windows partition in the event that you have one single partition. You'd be "splitting" your hard drive into two so that one part has Windows and the other has linux. Just ensuring you're crystal clear so you don't lose data as a result or anything.
Thanks for clarifying that :)

---

### Post by gorf 99 on 2008-03-15
Dual boot is wonderful.

I would suggest partitioning the hard drive in Windows first.  Leave the balance of the drive blank and Ubuntu will install on largest empty space.

1 caution though.  Grub (the boot loader) will be installed on the Windows partition if Windows is on the 1st part of the drive.  When you do a defrag in Windows may move Grub and you computer will not start.

If you have an extra smaller drive around.  Install Windows on the 2nd drive and install Ubuntu on the 1st drive. Grub will install on the Ubuntu drive.

---

### Post by RyviusRan on 2008-03-16
i have ubuntu install first so if I install window xp will it send a reply asking about splitting the HDD space?

---

### Post by talsemgeest on 2008-03-16
Ok, here are the steps you will have to take to install xp:

1. Partition your hard drive using Gparted.

2. Install xp onto the new partition.

3. Reinstall the grub bootloader.

4. Add xp to the bootloader.

As you can see it is quite a complicated process so you might want to consider doing a clean install of xp and then installing ubuntu

---

