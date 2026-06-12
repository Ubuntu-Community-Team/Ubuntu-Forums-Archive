---
title: "Trying to install Ubuntu"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Docfxit on 2008-02-11
I would like to install Ubuntu in a free partition I have created on hard drive.

MBR 5/5h Extended   9994 MB
        131/83h Linux Native  2054 MB
        131/83h Linux Native  7937 MB

I currently have XP and another version of Linux on different partitions on the drive.  

I'm using System Commander to select between OS's.

I choose  manual partitioning so I don't wipe out everything else I have on the drive.

During install under Prepare partitions it shows:
/dev/fd0
/dev/sda
With an error message saying "No root file system is defined.  Please correct this from the partitioning menu."

I don't see how to define a root file.

What do I need to do to get this installed.

Thank you,

Docfxit

---

### Post by taurus on 2008-02-11
If you highlight the partition that you want to mount as /, you would see below the window, the first one from the left, where you can edit it.  Click that and change the mount point from /media/sda5 (or whatever that is) to /.

---

### Post by Docfxit on 2008-02-11
> **taurus said:**
> If you highlight the partition that you want to mount as /, you would see below the window, the first one from the left, where you can edit it.  Click that and change the mount point from /media/sda5 (or whatever that is) to /.

Thank you for the reply.

When I have it highlighted I only have two options.

New partition table
Undo changes to partitions

Thank you,

Docfxit

---

### Post by Docfxit on 2008-02-11
If you are talking about doing things in GParted  I only see one line that I can select that is the entire hard drive and it shows a being Unallocated.  It doesn't show me the partitions that have XP and another version of Linux in them.

Thank you,

Docfxit

---

### Post by taurus on 2008-02-11
I am talking about during the installing process when you get to the partition part which you pick manual option, the last option.

---

### Post by Docfxit on 2008-02-11
> **taurus said:**
> I am talking about during the installing process when you get to the partition part which you pick manual option, the last option.

When I have it highlighted I only have two options.

/dev/sda

New partition table
Undo changes to partitions

Maybe the partition type I set up is not correct.  What type should it be?

Thank you,

Docfxit

---

### Post by LowSky on 2008-02-11
how did you install the other linux OS if you dont know what root (aka / )  is?

which partion is the free one? you will need to label it /

the others can renamed to you pleasing so that you can find them or define them more easily.

This wont effect their names in other operating systems.

---

### Post by Docfxit on 2008-02-11
I have two partitions set active.  Why is it only showing me one in the Prepare partitions screen?

/deb/sda                    "This is all the screen is showing me"

The partitions I have set as active are:

The first one is Linux Native (type (131/83h)
The second one is Linux Swap/Solaris (type 130/82h)

Does it need more partitions?
I'm using BootIt to setup the partitions.  I don't see how to format the partitions or to set one to boot from.

If it showed me all the partitions on the hard drive I could understand I need to label the one I want to boot from.  I have them labeled.  I don't see my labels.

Thank you,

Docfxit

---

### Post by Tyke91 on 2008-02-11
you only really need a / (root) partition and a swap partition for any linux distro.

go though and install ubuntu, when you get to the partition screen, select the partition that you want to edit and select mount as / .

---

### Post by Docfxit on 2008-02-11
> **Tyke91 said:**
> you only really need a / (root) partition and a swap partition for any linux distro.

go though and install ubuntu, when you get to the partition screen, select the partition that you want to edit and select mount as / .

I have a root partition and I have a swap partition.  When I get to the prepare partitions it doesn't have a way for me to edit and select mount as /


Thank you,

Docfxit

---

### Post by Docfxit on 2008-02-11
I'm looking for recommendations on software to partition a hard drive that will recognize my current partitions and add another partition for Ubuntu.

My current partitions are:

Part 0 XP Pro
Part 1 Extended  For Rpath
            Linux Native 
            Linux Native
           Linux Swap/Solaris
Part 2 Linux Native   For Ubuntu
Part 3 Linux Swap/Solaris


The GParted that comes with Ubuntu doesn't recognize the current partitions.
It's showing the entire hard drive as unallocated. 

Thank you,

Docfxit

---

### Post by dstew on 2008-02-11
How are you running gparted? Is it from a Live CD boot? It will not run properly if you start it from a hard-disk boot.

---

### Post by Docfxit on 2008-02-11
> **dstew said:**
> How are you running gparted? Is it from a Live CD boot? It will not run properly if you start it from a hard-disk boot.

I'm running it from the Live CD boot.

Thank you,

Docfxit

---

### Post by dstew on 2008-02-11
That is strange, that gparted cannot see your partitions. Maybe the program is not working as it should. There is another partitioner, fdisk, that uses a text interface. Post the output of the command```
sudo fdisk -l
```to see if fdisk can see the partitions.

---

### Post by Docfxit on 2008-02-11
I found that Ubuntu install destroyed my other Linux install.  I deleted those partitions and now GParted is working.

I would like to install the boot loader to the root partition instead of the MBR.  The default is:
The MBR (hd0)
What can I put in for the boot loader partition?

Thank you,

Docfxit

---

### Post by dstew on 2008-02-11
If the root partition is (hd0,0) then tell grub to install there. You have to know the grub name for that partition. If I see your fdisk -l output, I can tell you the probable name. Remember, grub counts starting at zero, so the first partition of your first disk would be (hd0,0).

I assume you want to install the grub boot loader into your partition rather than your MBR because you have another boot loader in your MBR that you are already comfortable with, and that has multi-boot capability.

---

### Post by Docfxit on 2008-02-11
How can I run Fdisk from the live CD?  I don't see a command line and I don't see the application fdisk.

Thank you,

Docfxit

---

### Post by dstew on 2008-02-11
Open a terminal window (Applications --> Accessories --> Terminal) and enter the command **sudo fdisk -l** on the command line.

---

### Post by Docfxit on 2008-02-11
> **dstew said:**
> If the root partition is (hd0,0) then tell grub to install there. You have to know the grub name for that partition. If I see your fdisk -l output, I can tell you the probable name. Remember, grub counts starting at zero, so the first partition of your first disk would be (hd0,0).

I assume you want to install the grub boot loader into your partition rather than your MBR because you have another boot loader in your MBR that you are already comfortable with, and that has multi-boot capability.

Yes.  That is correct.  I have System Commander in the MBR.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ef67c30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       28011   224990208    7  HPFS/NTFS
/dev/sda2           28012       28265     2040255   83  Linux
/dev/sda3           28266       28329      514080   82  Linux swap / Solaris

---

### Post by Docfxit on 2008-02-11
I asked it to install the boot loader into (hd0,1) .

System Commander can't find the boot loader.
I did change the second partition to /
I did go into System Commander's settings menu and selected the Linux partition and turned on Bootable with ALT-T
Any ideas?


Thank you,

Docfxit

---

### Post by dstew on 2008-02-12
> I asked it to install the boot loader into (hd0,1)That seems correct to me. I don't know anything about System Commander though. Maybe you have to configure it properly.

You can try to boot the Linux partition using a [supergrub disk]("http://supergrub.forjamari.linex.org/"), or even a [grub floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy") to check if it works OK.

---

### Post by Docfxit on 2008-02-12
Thank you for the reply.

Thank you, 

Docfxit

---

