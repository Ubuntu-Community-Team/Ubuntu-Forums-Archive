---
title: "[SOLVED] Install Kubuntu over Ubuntu"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by five_tools on 2008-02-13
My machine is dual-boot (XP & Ubuntu).  I installed KDE onto Ubuntu, and found the combination a little messy.  I'd like to try a clean install of Kubuntu, alone.

The most natural thing would be to install Kubuntu in Ubuntu's place.  I ran installation from the Kubuntu Live CD.  But, when I choose Ubuntu's partition as the partition to install Kubuntu on, I get this error:

[IMG]http://img406.imageshack.us/img406/8645/snapshot2ao7.jpg[/IMG]

What do I need to do to fix it?

---

### Post by luisromangz on 2008-02-13
You need to change the /dev/hda2 partition's mountpoint from /media/hda2 to /, which is the root filesystem.

---

### Post by jaytek13 on 2008-02-13
If your just trying to install it over Ubuntu complete, I'd recommend just deleting /dev/hda2 and /dev/hda5 and then telling Kubuntu to use the extra space. You seem to have selected the option to manually specify the partition table. If that is the route you were going, you would follow the directions at the bottom. specifiying you need a / partition , a swap partition, and then you would also need a /home partition.

---

### Post by five_tools on 2008-02-13
> **luisromangz said:**
> You need to change the /dev/hda2 partition's mountpoint from /media/hda2 to /, which is the root filesystem.

I did that.  But, the install program shut down prematurely.  Now there's a /dev/sda device.

[IMG]http://img266.imageshack.us/img266/706/snapshot3fi9.jpg[/IMG]

---

### Post by five_tools on 2008-02-14
Problem solved.  There was a stain on the Live CD.

I'm getting a GRUB error now, but I started a new threat for that:
[http://ubuntuforums.org/showthread.php?p=4331146&posted=1#post4331146]("http://ubuntuforums.org/showthread.php?p=4331146&posted=1#post4331146")

---

