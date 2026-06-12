---
title: "Ubuntu on a Maxtor OneTouch III"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Psyha on 2006-09-09
Could I install Ubuntu on a Maxtor One-Touch III backup drive, while still having windows usuable on my normal hard drive and the ability to use the maxtor with windows?

Basic information:

Ubuntu on maxtor.

Windows on hard drive.

Be able to boot from maxtor or hard drive relatively easily.

Be able to back up files from windows onto maxtor without ubuntu interfering.

Would this be possible without ANY repurcussions?

---

### Post by bodhi.zazen on 2006-09-09
Yes. Partition a FAT partition for data 9easiest share with Windows and Ubuntu).

Separate partition for Ubuntu. Ubuntu 10-20 Gb is fine, can make due with less if needed.

---

### Post by Psyha on 2006-09-10
Great, I assume I can do that straight from the live CD?

---

### Post by bodhi.zazen on 2006-09-10
> **Psyha said:**
> Great, I assume I can do that straight from the live CD?

Yes, only 1 potential issue: if this is a usb drive you need to set your bios to boot to a usb drive. If it is an internal drive you should be good to go.

---

### Post by Psyha on 2006-09-11
Great, I just enter the BIOS and set to boot from the maxtor drive, and there is a button on the ubuntu home screen to transfer to the main hard drive?

---

### Post by bodhi.zazen on 2006-09-11
> **Psyha said:**
> Great, I just enter the BIOS and set to boot from the maxtor drive, and there is a button on the ubuntu home screen to transfer to the main hard drive?

Not sure I understand the question.

What I would advise is for you to partition your maxtor drive such that there is a FAT32 partition for "data". This can be shared and used by with both Windows and Ubutnu. Size = Most of the drive.

You will need a swap partition, typically RAM x2, no > 1 Gb is typical.

And a partition "root" for Ubuntu; AKA "/". Size = 10-20 Gb.

When installing Ubutnu you will use manual partitioning and define a "mount point" for the data/FAT 32 partition. You can use whatever schem you like, but I suggest you start with something simple like "/mnt/data". Your data (in Ubuntu)will be located in /mnt/data and (in Windows) likely "E:\".

You can use a more complicated partitioning scheme, but it is not needed.

When you are installing Ubuntu, you will install GRUB to the MBR of your windows drive (Grub = (HD0,0) Linux = /dev/hda1) and you will then be a "dual-booter" in that each time you boot you will see a GRUB menu asking which OS to boot.

You will boot from the MBR on the Windows drive.

MBR = Master Boot Record.

Is this what you are asking?

---

### Post by gn2 on 2006-09-11
I use PCLinuxOS (and LiLo boot loader) on a USB hard drive, because it's a very easy install process.

I wasn't able to get Ubuntu and Grub to load on USB drive easily. 
(that's not to say it can't be done)

You need to check that booting from USB is enabled in your BIOS settings, and the USB drive is before the internal drive in the boot order.
If installing PCLinuxOS, disconnect power to internal drive first.
Once installed switch off and re-connect power to internal drive.

You can now select which drive to boot from by having the USB drive on or off at boot time.

---

### Post by Psyha on 2006-09-11
From what it looks like, you need ot buy a 60$ program to partition a drive? Is there an easier/less costly way to do it? if so, how?

---

### Post by bodhi.zazen on 2006-09-11
LOTS !!!

[Gparted](http://gparted.sourceforge.net/)

Gparted is on the Ubutnu Live cd.

Use Gparted to re-size your windows partition.

Gparted will add and format partitions.

Alternate: fdisk. fdisk in used form the CLI. It worked better then Gparted has in the past, but takes a little time to learn.
[fdisk](http://www.freeos.com/articles/3935/)

[cfdisk](http://www.linux.com/howtos/IBM7248-HOWTO/cfdisk.shtml)

---

### Post by Psyha on 2006-09-11
Ok, Here is what I understand so far:

Create a partition sized 100gb as a shared files between ubuntu and windows. It will be of FAT32 type.

I will make a swap partition. I have no idea what you mean by this because i have never installed OSs before, so could you please explain this in idiot-speak for me?

Make the ubuntu partition to store the OS files. I think i'll make it a good 20 gigs, but I don't know how to name it or have ubuntu recognize it.

If you have the time, it would be nice to make a step-by-step list, but I doubt that would fit into your schedule. Thanks!

---

### Post by bodhi.zazen on 2006-09-11
> **Psyha said:**
> Ok, Here is what I understand so far:

Create a partition sized 100gb as a shared files between ubuntu and windows. It will be of FAT32 type.

I will make a swap partition. I have no idea what you mean by this because i have never installed OSs before, so could you please explain this in idiot-speak for me?

Make the ubuntu partition to store the OS files. I think i'll make it a good 20 gigs, but I don't know how to name it or have ubuntu recognize it.

If you have the time, it would be nice to make a step-by-step list, but I doubt that would fit into your schedule. Thanks!
The Ubuntu installation process will do the swap and ubuntu partitioning in the free space you create automatically.

for a graphical guide try this:

[Graphical Ubuntu Install guide](http://www.psychocats.net/ubuntu/installing.html) [color=red]Thanks aysiu[/color]

---

### Post by Psyha on 2006-09-12
Also, can GParted rejoin the partitions if something were to go wrong?

---

### Post by bodhi.zazen on 2006-09-12
Yes. You would likely re-partition.

---

### Post by Psyha on 2006-09-12
Will GParted join partitions if something goes wrong?

---

### Post by bodhi.zazen on 2006-09-12
> **Psyha said:**
> Will GParted join partitions if something goes wrong?

Since no one else has answered...

Yes, if I am understanding your question GParted will do this.

Say you now have 1 partition= 20 Gb ntfs for windows. You re-size it and create a 10 Gb ntfs partition with windows and 10 Gb "free space".

You will then use the 10 gb free space for Ubuntu, at least /swap and / Say swap = 1 Gb and / = 9 Gb.

Now say you install Ubuntu and later decide it is not for you. You could use Gparted to re-partition which would involve deleting the 2 ubuntu partitions so you would then have 1 10 Gb ntfs and 10 free space.

You would then re-size and have a single 20 Gb ntfs partition again.

You would need to re-install the MBR with a windows CD or you would not be able to boot.

In the past you would not have been able to delete the ntfs partition and add that free sapce to Ubuntu /. The new version of Gparted claims to allow this. Use with caution.

Clear as mud? :)

---

