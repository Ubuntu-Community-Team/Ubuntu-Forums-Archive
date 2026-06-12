---
title: "Can't install Linux (Any Linux)."
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by RussianVodka on 2006-08-20
Yesturday everything was working perfectly.

So, I decided to completely whipe my HD and install Sabayon Linux on it. But due to a well known bug, it froze in the middle of installation. I read their forum, and apperantly alot of people get that bug, and there is realy no way around it.

So, I say "Oh well" and start installing Ubuntu again (before it was sharing space with Windows which I never used, now it will be by itself). 15% into installation, I get an error which states "Failed to create file system.". I tried installing Ubuntu several more times, and the same thing happened. (A screenshot of the error is in the attachment).

So I dusted off my old Fedora Core 5 DVD, and started installing that. The installation went very well. But when I tried to boot it up, it crashed at some point (I'll check again and post what it said).

And, well, I tried installing Ubuntu again, and I still get the same error at 15%.

Oh, and it should be mentioned that before installing Sabayon I enabled Native SATA support in my BIOS (It had to be disabled before because Windows wouldn't work with it enabled). But I've installed Linux with it enabled before, and everything worked fine.

Does anyone know what to do?

Oh yeah, when ever I boot up any Linux, I get strange errors about memmory allocation, or something like that. I'll take a photo of them when I reboot. They haven't bothered me before, but maybe it's a sign of my (1 month old) hardware deteriarating.

---

### Post by taurus on 2006-08-20
Have you already created filesystem for Ubuntu?  Perhaps you should use the alternate CD to install Dapper on your machine since it gives you a little more control of how to partition your harddrive.

---

### Post by RussianVodka on 2006-08-20
> **taurus said:**
> Have you already created filesystem for Ubuntu?  Perhaps you should use the alternate CD to install Dapper on your machine since it gives you a little more control of how to partition your harddrive.

When asked to "Prepare Disk Space" I select "Erase entire disk".

Then I get this:

```

Language: English
Keyboard layout: us
Name:********
Login name: ********
Location: America/New_York
Partitioning:
  If you continue, the changes listed below will be written to the disks.
  Otherwise, you will be able to make further changes manually.

  WARNING: This will destroy all data on any partitions you have removed as
  well as on the partitions that are going to be formatted.

  The following partitions are going to be formatted:
     partition #1 of /dev/sda as ext3
     partition #5 of /dev/sda as swap

```

Then I click "Install" and it starts installing. And then later crashes.
The last time I manualy edited my partitions, I was installing Gentoo... And that didn't go so well. So I'd prefer the computer to do it for me :D.

---

### Post by esqueleto on 2006-08-31
I have the same problem with Ubuntu and FC5.

With ubuntu the problem is stupid, because I cannot use the Disk Partition Application. If I use it alone I get the same error. Looks like that Ubuntu can't format my disk.

What can I do? What I'm doing wrong?

tkx in advance
Paulo Aboim Pinto
Odivelas - Portugal

---

### Post by Carbonfish on 2006-08-31
Well, until esqueleto showed up with the same problem, I was going to suggest that perhaps your HDD was dying. Now I am not sure. Since you are wiping the drive anyway do you have another drive that you can mount and see if that changes the picture?

I'm afraid that's all I have.

KC

---

### Post by John.Michael.Kane on 2006-08-31
Looks like there's an issues with the live/cd install. have you tried the alternate/cd install?

---

### Post by tatimmer on 2006-08-31
I have a knoppix live cd which has "qtparted" on it.  This works very well for deleting partions creating free space.  There is also "gparted" and parted.  Not sure what the Ubuntu live has on it but must be one of these.

---

### Post by b_martinez on 2006-08-31
Try this, while using the "live-cd"

sudo fdisk /dev/hda

if 'not found' comes up try 

sudo fdisk -l

That is a lower case "L" at the end of the command. It will list all mounted hard drives and their partitions. Choose the one you are going to use. It may be /dev/sda for a sata drive. If so then 

sudo fdisk /dev/sda

once fdisk starts, type 'm' (without quotation marks) for a list of commands. 
 The 'd' will delete a partition. If you are going to do a full install, just delete everything. You will be required to select a partition number for all but the last partition. When done, just type in 'w' to write the changes, and then 'q' to quit. Once your hard drive is clean, the installer should have no problems partitioning/formatting the hard drive.
Hope this maybe helps
Bill

---

### Post by kelean on 2006-08-31
I have had simuler  problems tring to install ubuntu.  I found out that I had to remove all of the existing partitions then create new partitions before the install would work.

---

### Post by bodhi.zazen on 2006-08-31
I have had these type of problems using GParted to partition. I think it is in the way GParted creates a partition table?

Now I always use fdisk to partition and these problems do not happen to me any longer.

If you want a nice GUI to partition I have partitioned with the SUSE install CD and it works well. Carefull though or you will install SUSE (I abort after partitioning).

Limited experience with other distro's since fdisk is not hard to use.

---

