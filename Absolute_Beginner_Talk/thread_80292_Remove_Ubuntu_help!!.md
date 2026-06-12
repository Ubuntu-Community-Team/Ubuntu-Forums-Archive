---
title: "Remove Ubuntu help!!"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by billtemp on 2005-10-21
I am removing Ubuntu from an old PC (due to not being able to get a USB WLAN to work) and am reloading windows 95.

I find that although I have a active DOS partition made, when booting up the PC tries to start with Grub and then halts as I have reformatted everything in sight.

There is a small partition on the c: drive that I can not delete, name, format etc that is probably the problem.

Can anyone tell me how to remove the Grub startup or how to remove the small partition.


thanks
Bill

---

### Post by yaye on 2005-10-21
[QUOTE=billtemp]I am removing Ubuntu from an old PC (due to not being able to get a USB WLAN to work) and am reloading windows 95.

I find that although I have a active DOS partition made, when booting up the PC tries to start with Grub and then halts as I have reformatted everything in sight.

There is a small partition on the c: drive that I can not delete, name, format etc that is probably the problem.

Can anyone tell me how to remove the Grub startup or how to remove the small partition.


thanks
Bill[/QUOTE]

Hello,

Get a DOS boot disk from bootdisk.com:

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

If you have a large drive ( > 32 Gigabytes ), use a Windows 98 version.

After making the bootdisk, change the BIOS of the computer to boot from the floppy disk drive first.  Put the disk in and after the computer boots to the DOS prompt, type:

fdisk /mbr

then hit the Enter key.

This should erase Grub from the MBR.

To remove a partition, you can download the System Rescue CD:

[http://www.sysresccd.org/](http://www.sysresccd.org/)

It has qtparted on it, which is a clone of Partition Magic.  After Burning the CD, you can boot from it.  I believe the command to start qtparted is:

run_qtparted

Gives you a nice GUI for partitioning your drive.  Screenshots here:

[http://www.sysresccd.org/screenshots.en.php](http://www.sysresccd.org/screenshots.en.php)

Ian

---

