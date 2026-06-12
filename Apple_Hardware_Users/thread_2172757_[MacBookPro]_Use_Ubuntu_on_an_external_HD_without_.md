---
title: "[MacBookPro] Use Ubuntu on an external HD without any system modification ?"
date: 2013-09-06
forum: Apple Hardware Users
---

### Post by RedVivi on 2013-09-06
Hello,


I have a mid-2010 MBP with Mountain Lion installed.
I would like to use Ubuntu from time to time, without dual boot, as I would like to keep my MBP as clean as possible.


Is it possible to boot/use Ubuntu from an external HD _without modifying at all_ the Mac system ? Is there some limitations ?

Is there any recent tutorial around ?


Regards,
redvivi

---

### Post by sudodus on 2013-09-07
If you can boot from a USB pendrive, you can also boot an installed system (or a live system) on a USB hard disk drive or SSD.

So download a suitable iso file, make a USB boot drive and try it (without any installation in the first step. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

Maybe the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971") would suit your needs to install a bootable Ubuntu based system on a USB drive.

I don't know what kind of architecture it is, Intel/AMD (not PowerPC), EFI or BIOS ... You would have problems running the OBI, which needs BIOS, if you have an EFI system, and it won't run in PowerPC.

---

### Post by DoubleClicker on 2013-09-20
None of the tutorials above have any relevance to your question.  ALL Macs manufactured after 2006 are EFI systems, that require GPT partition tables to boot.  The tutorials above are relevant only on systems that have BIOS, which macs do not.

As long as the USB drive is formatted with a GPT partition table and has the required EFI partition, then there should be no problem booting from an external USB device, whether it is a pendrive or a hard drive.  The easiest way to ensure this, is to use Disk Utility in OS X to partition the drive.

Installing Ubuntu on the external USB drive, will be the same as installing Ubuntu on the internal drive.

---

### Post by sudodus on 2013-09-20
> **DoubleClicker said:**
> None of the tutorials above have any relevance to your question.  ALL Macs manufactured after 2006 are EFI systems, that require GPT partition tables to boot.  The tutorials above are relevant only on systems that have BIOS, which macs do not.

As long as the USB drive is formatted with a GPT partition table and has the required EFI partition, then there should be no problem booting from an external USB device, whether it is a pendrive or a hard drive.  The easiest way to ensure this, is to use Disk Utility in OS X to partition the drive.

Installing Ubuntu on the external USB drive, will be the same as installing Ubuntu on the internal drive.

Your comment is correct concerning the OBI, but the following links are general, not limited to MSDOS partition tables with MBR or 32-bit systems. Read them and you will find out :-)
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
https://help.ubuntu.com/community/In...n/FromUSBStick[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=1958073"]Ubuntu Forums tutorial "Howto make USB boot drives"
[/URL]
For example, in the first link there is a reference to this current Ubuntu Forums Thread

[Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac]("http://ubuntuforums.org/showthread.php?t=2174630")

---

### Post by DoubleClicker on 2013-09-23
> **sudodus said:**
> Your comment is correct concerning the OBI, but the following links are general, not limited to MSDOS partition tables with MBR or 32-bit systems. Read them and you will find out :-)
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]
https://help.ubuntu.com/community/In...n/FromUSBStick[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=1958073"]Ubuntu Forums tutorial "Howto make USB boot drives"
[/URL]
For example, in the first link there is a reference to this current Ubuntu Forums Thread

[Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac]("http://ubuntuforums.org/showthread.php?t=2174630")

They are still irrelevant.   True the first contains a link, to a tutorial, on how to make a USB live disk for a mac. That would be useful, if that was the question he was asking, but it wasn't .  The question was how to make a bootable installed system.  I am assuming that he either can make a live disk (CD or USB), or would ask about it, if he can't.

Incidentally the above mentioned tutorial, would still requires a USB stick that had a proper GPT-partition table, which it fails to mention.

---

### Post by Quackers on 2013-09-23
To the OP. Yes it is entirely possible. Not sure about a specific tutorial, as such. If you install to a USB device make sure that the grub bootloader is installed to the mbr of that drive and not your Mac's drive (which would fail anyway). In other words you would have to use the "something else" option at the partitioning phase of the installation and at the bottom of that page make sure that grub is installed to the drive you are installing Ubuntu on and not your Mac. It will default to /dev/sda, which in your case is likely to be your Mac's drive.
The USB flash drive can be formatted in fat32 and in mbr. It is not necessary to have a gpt.

DoubleClicker
my tutorial linked to by sudodus does not mention anything about gpt partitioning because it is not required. In fact the USB devices I have used so far have been formatted as fat32 and are MBR formatted, as stated in the guide.
It would be a bit silly to refer to writing Syslinux to the mbr of a flash drive that was formatted gpt. Such a device would not have a mbr, save for the protective mbr that gpt requires, and you wouldn't want to write to that.
With regard to your point about the bootable USB device for Ubuntu - the point is that the OP wouldn't necessarily know that his Ubuntu live USB may not boot on his Mac until it was tried.

---

### Post by DoubleClicker on 2013-09-24
> **Quackers said:**
> 
DoubleClicker
my tutorial linked to by sudodus does not mention anything about gpt partitioning because it is not required. In fact the USB devices I have used so far have been formatted as fat32 and are MBR formatted, as stated in the guide.
It would be a bit silly to refer to writing Syslinux to the mbr of a flash drive that was formatted gpt. Such a device would not have a mbr, save for the protective mbr that gpt requires, and you wouldn't want to write to that.
With regard to your point about the bootable USB device for Ubuntu - the point is that the OP wouldn't necessarily know that his Ubuntu live USB may not boot on his Mac until it was tried.

That is surprising to me, that you have gotten it to work.  In 7 years, since Apple adopted EFI, I've not been able to get any USB drive to boot, that wasn't partitioned as GPT.  

With Disk Utility in OS X; if you partition your drive, as GPT with a FAT32 partition, it creates a hybrid MBR.  So Syslinux will write to the hybrid MBR.

---

