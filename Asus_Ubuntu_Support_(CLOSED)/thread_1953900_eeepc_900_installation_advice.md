---
title: "eeepc 900 installation advice"
date: 2012-04-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by coldraven on 2012-04-07
I want to install Ubuntu on a friends eeepc 900 and I have Googled a few tips but I would like to be sure that I do it right.

On the 4GB drive I notice that there is a partition named BIOS, is it OK to delete all the partitions and use the entire disk?

To free up space what other folders should I mount on the 20GB drive and is that actually possible to do at install time?
What should I do about the swap partition? 

Has anybody tried 12.04 beta and is that the best distribution to install?

My friends are only here for a short time otherwise I would wait until 12.04 is released later this month.
All advice gratefully received. Thanks

---

### Post by peterqb on 2012-04-07
I wouldn't delete the BIOS partition, as it contains important data to enable the computer to boot up. The first part of this is in a ROM, but then the computer will look at any data there to get the right order of device to boot from (disk, CD, network). If it can't find this you might find that nothing will happen.

See if you can get it to boot from your Ubuntu .iso and install. You can delete partitions (not the BIOS!) later, but always be very careful when doing this, as a mistake cannot be undone.

Good luck.

I'm trying to get an Asus eec to recognize and boot from either an external drive or a pen drive, but the BIOS preferences won't allow it to do this.
--
pqb

---

### Post by JRV on 2012-04-07
The 4 gig drive is faster but too small for a normal installation, and the larger drive is slow.


On my 701 and 901 I wiped the drives and used the netboot installation disk.

Here is my thread describing the process:

 [http://ubuntuforums.org/showthread.php?t=1876241](http://ubuntuforums.org/showthread.php?t=1876241)


After installation it is possible to migrate /home to the larger drive.

---

### Post by coldraven on 2012-04-07
> **peterqb said:**
> I wouldn't delete the BIOS partition, as it contains important data to enable the computer to boot up. The first part of this is in a ROM, but then the computer will look at any data there to get the right order of device to boot from (disk, CD, network). If it can't find this you might find that nothing will happen.

See if you can get it to boot from your Ubuntu .iso and install. You can delete partitions (not the BIOS!) later, but always be very careful when doing this, as a mistake cannot be undone.

Good luck.

I'm trying to get an Asus eec to recognize and boot from either an external drive or a pen drive, but the BIOS preferences won't allow it to do this.
--
pqb
Thanks for the advice but I'm confused, I thought that BIOS lived in a chip on the motherboard rather than a partition of the hard disk. What's that about?

---

### Post by Plumtreed on 2012-04-08
If you want to you can use the entire disk to install Ubuntu or other system. The normal install process usually asks if the entire disk should be used and therefore wiped, formatted.

There may be a more suitable OS for such a limited machine but this, of course, is your choice!

@peterqg   just follow the normal install process to install an OS to an eternal flash drive. Most will ask you where to install grub and you need to select the external drive in order to boot.

---

### Post by coldraven on 2012-04-12
I ended up installing Xubuntu 11.10 and my friend is very happy with it.
Everything worked straight away.
I kept the 85MB BIOS partition on the 4GB drive and after install had 1.5GB free space.
I just read that this partition is to enable the Boot Boost function.
[http://en.gentoo-wiki.com/wiki/Asus_Eee_PC_1000HE](http://en.gentoo-wiki.com/wiki/Asus_Eee_PC_1000HE)

If anyone could tell me how to hide the BIOS partition from Thunar I would be very happy.
I'll mark this as solved, thanks to all for your input.

---

