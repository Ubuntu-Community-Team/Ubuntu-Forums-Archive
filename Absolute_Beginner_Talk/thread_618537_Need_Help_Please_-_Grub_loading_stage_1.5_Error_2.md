---
title: "Need Help Please - Grub loading stage 1.5 Error 2"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by ajenks on 2007-11-20
I attempted to install Ubuntu (I have now also attempted Linux Mint) onto my Windows XP desktop.  Unfortunately, I selected guided partition setup, instead of manual, since I didn't know what I was doing.  My intent was to create a dual boot machine given all of the great things I have read about Ubuntu.  I obviously did not realize this attempt would completely wipe out Windows.

I have now tried burning many cds with the recent release of Ubuntu, as well as Linux Mint 4.0.  I can get my desktop to boot with the live cd in the machine and I have been "successful" at completing the install from the live cd.  However, I have never been able to get past the reboot phase after the install.  Each and every time I get the same error: GRUB loading stage 1.5 Error 2 and the system hangs.

Unfortunately, this has left me with a scream Velocity Micro pc that no longer has Windows, won't boot with my Windows Recovery CD, will only boot with an Ubuntu or Linux Mint live cd, but will not successfully boot into either of those OSs on the hard drive.  Pretty much left with a helpless machine that I can't seem to solve.

Any specific help would be significantly appreciated!  My Velocity Micro support technician is stumped as well.

Thanks much, Alan

---

### Post by MegaJim on 2007-11-20
I'm concerned that I've seen a few reports like this, that people are unable to boot from their windows CDs...  You can try cycling the power for a minute or so and trying to boot from your CD drive again.

First obvious question is: have you set the BIOS to boot from the CD drive first?

edit: hmm never mind you said recovery CD; if its not a genuine windows install cd this might explain it, probably some ghost partition tomfoolery.

this guide tells you how to repair grub: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

give that a go

---

### Post by Duck2006 on 2007-11-20
Have you tryed reinstalling grub again?

---

### Post by twiceasworn on 2007-11-20
Well I am not sure why it would be doing this, since error two means it cant find your hard drive.

[Source]("http://www.uruk.org/orig-grub/errors.html")

---

### Post by ajenks on 2007-11-20
I have cycled power, done rain dances, you name it for the last week.  Yes, it is setup to boot first from cd, which is why I have no problem using the live cds to run the distros.  My hope was that if I could finally get Ubuntu or Linux Mint fully installed and operational on the hard drive, versus running off of the cd and not being able to make changes, etc., then it may allow me and the pc help tech go attack the Windows issue, which is obviously huge since I cannot run Windows, my data is lost, etc.

---

### Post by ajenks on 2007-11-20
how do I just reinstall GRUB?  Isn't that an issue, when the only way I can run Ubuntu is off of my live cd?

---

### Post by MegaJim on 2007-11-20
you can restore grub using the live CD, some sata controllers confuse grub and it gets things backwards.

---

### Post by Duck2006 on 2007-11-20
This may help

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ajenks on 2007-11-20
MegaJim, 

I went through the process the link you posted takes you through for installing GRUB.  The terminal window said everything was successful, etc.  However, I reboot without the cd and still get the same GRUB error.

---

### Post by MegaJim on 2007-11-20
There is probably something wrong with grub's assumptions about something or other.

Could you do us a favour and post the output of:

```
cat /boot/grub/device.map
```

and

```
sudo fstab -l
```

---

### Post by Duck2006 on 2007-11-20
From the live cd in the terminal type

sudo fdisk -l t

and

cat gedit /boot/grub/menu.lst

and post the outputs

---

### Post by ajenks on 2007-11-20
unfortunately (I am assuming), the first command ending in device.map returned "no such file or directory" and the second command returned "command not found"

---

### Post by ajenks on 2007-11-20
I got nothing as well on Duck's command suggestions.

---

### Post by Duck2006 on 2007-11-20
Sorry this

sudo fdisk -l t

should be this

sudo fdisk -l

---

### Post by ajenks on 2007-11-20
mint@mint:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by ajenks on 2007-11-20
sorry......

mint@mint:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003de50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000015

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8666    69609613+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x725bcd19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29645   238123431   83  Linux

---

### Post by Duck2006 on 2007-11-20
> sudo fdisk -l

The -l is the small letter "L"

---

### Post by Duck2006 on 2007-11-20
> **ajenks said:**
> sorry......

mint@mint:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003de50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000015

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8666    69609613+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x725bcd19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29645   238123431   83  Linux

What drive have you set in your BOIS to boot from?

---

### Post by ajenks on 2007-11-20
the cd rom is 1st boot

---

### Post by Duck2006 on 2007-11-20
cdrom then what hard drive?

You may hve to do a reinstall of ubuntu. Partition the drive first and when it comes to the partition part use the partition you have made for it. install windows first, then ubuntu.

This should help

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by ajenks on 2007-11-20
I am having difficulty getting my Windows XP original cd to work for some reason.  So, oddly enough (maybe not), my initial concern is getting Ubuntu up and running appropriately and then go from there.  Does that make sense or create more issues?

---

### Post by Duck2006 on 2007-11-20
> **ajenks said:**
> I am having difficulty getting my Windows XP original cd to work for some reason.  So, oddly enough (maybe not), my initial concern is getting Ubuntu up and running appropriately and then go from there.  Does that make sense or create more issues?

What drive did you install ubuntu to?

---

