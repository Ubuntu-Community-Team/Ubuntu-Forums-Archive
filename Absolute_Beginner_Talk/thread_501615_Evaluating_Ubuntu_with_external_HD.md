---
title: "Evaluating Ubuntu with external HD"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by henrywm on 2007-07-15
I am considering a switch to Linux, probably Ubuntu. I tried Ubuntu and other distros on an old laptop with 1.7Ghz and 256 MB RAM, but they were all slow. I have another laptop with 2 GHZ and 1 GB RAM. It uses Windows XP. For now I need to keep it intact, and so I thought of installing Ubuntu on an external hard drive, which I would need to connect by USB. Is that possible? If so, which brand of external hard drive do you recommend? Are there some which Ubuntu does not support?

---

### Post by Happy_Man on 2007-07-15
If it can be found by Windows, it can be found by Ubuntu. That's the rule as far as hard drives go. 

The problem, though, will be for you to get the bootloader working correctly. Try this guide that walks you through the process. It's a bit dated, but should still be OK: [http://www.pcmech.com/article/installing-ubuntu-linux/page-1.htm](http://www.pcmech.com/article/installing-ubuntu-linux/page-1.htm)

---

### Post by wolfen69 on 2007-07-15
Xubuntu [http://www.xubuntu.org/](http://www.xubuntu.org/) will run just fine on that older laptop. it is a "lightweight" distro made to use less system resources.

---

### Post by sdowney717 on 2007-07-15
if you were using the live cd it will be slow.
I dual boot it on my daughters computer an old 660mhz pentium 3 and it works much faster than xp pro..

why not simply use the partitioner and set it up in another partition on the main drive?

---

### Post by henrywm on 2007-07-15
What does Xubuntu have that Ubuntu doesn't, aside from Gnome?

I was not using the Live CD. It was fully installled.
I did not want to partition my drive on my newer laptop for two reasons:
   1) It is using NTFS. I heard that moving that partition without reformatting can be difficult.
   2) I would prefer to keep that computer intact for now, because I need it for school.

---

### Post by cotcot on 2007-07-15
[This]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") works for installing ubuntu on a usb pendrive. It should work on an external usb hdd also. 
I have for example gentoo on an external hdd with lilo as bootloader. I had to fiddle with the bootloader. What I did to get the gentoo running is basically not different from getting ubuntu running. I did not get out of it with grub because of a mix of sata and ide drives. With lilo is was ok just by following the manual.

---

### Post by sdowney717 on 2007-07-15
I have setup ubuntu on 3 systems that are NTFS.

What I did was 
check the NTFS partition for errors run chkdsk from properties and it will do this at windows boot
defrag the NTFS partition to make sure files are more or less contiguous

then the trick is to create free unallocated space by shrinking the NTFS partition.
I agree, it is a little confusing.

The least confusing way is for me:
boot the live cd, click install
when you get to hard disk discovery and partition select the manual option
When I did this I shrunk the windows NTFS partition to create free space, it shows you a visible bar graph and lets you select the size of the new ext3 partition and size of the old NTFS partition.
What I find confusing is the next step where it tells you to select mount points, SO the easiest thing is once it is resized simply reboot the live CD.
Just cancel the install, the drive has been resized.

Then start the install process again and tell it to use all the unallocated free space I had made on the last boot of the live cd.

And that is that.

---

### Post by mdsmedia on 2007-07-15
Great hint, sdowney. The mount points are probably the most confusing for anyone installing on a drive with Windows on it.

I've managed to do it after a few tries each time I've installed Ubuntu, but I never seem to get it first time.

The first rule is BACKUP your data and important files on Windows. The 2nd rule is backup your data and important files on Windows. Then if you make a mistake in partitioning and resizing your NTFS partition you won't have lost anything.

In all my installations of Ubuntu I've never lost anything in Windows, but the 3rd rule is...BACKUP.

---

### Post by henrywm on 2007-07-15
> **wolfen69 said:**
> Xubuntu [http://www.xubuntu.org/](http://www.xubuntu.org/) will run just fine on that older laptop. it is a "lightweight" distro made to use less system resources.

What are the differences between Ubuntu and Xubuntu, aside from XFCE?

---

### Post by kingcharles1666 on 2007-07-17
Hi,

I have done the exact same thing (installing ubuntu on an external HD)
It was real easy!

The way I went about it was:
1)remove the internal Hard Drive of the laptop (so no HD inside!)
2)connect the usb drive you want to install ubuntu to(see note below)
3)boot from the alternate CD (i prefer it to the live one personally)
4)do the install as if you were installing a normal pc.
5)when finished shut down and put the internal Hard Drive back into the machine
6)set up the bios to show the bootable devices attached/installed

now when my laptop boots (HP NC6220) it will show a list of devices at boot time and when I select the internal disk it will boot xp and when I select the usb drive it will boot ubuntu.
I used a very cheap usb 2.5" external drive and I think that any drive recognised by linux/bios will do

Two Notes:
1) the ubuntu install will not have your internal drive in fstab so you will not be able to mount it automatically but you can fix this manually or wait for a distribution upgrade (I went from edgy to feisty on my external drive while the internal HD was installed and that added the internal disk to fstab)
2) you must connect your external drive always to the same usb port (which you used during install) or it will give errors.

---

