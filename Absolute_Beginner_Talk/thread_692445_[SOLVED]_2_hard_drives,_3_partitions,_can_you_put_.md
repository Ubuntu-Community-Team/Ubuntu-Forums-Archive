---
title: "[SOLVED] 2 hard drives, 3 partitions, can you put logical accross both drives?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Ringo1508 on 2008-02-09
Ok, so I've used the search tool on this forum and have even tried to google for the answer. So far I've learned that you can boot from physical partitions but not logical. I've also learned that you can only have 4 physical partitions, but you can have more if you use logical partitions.

From everyone's recomendations, it's a good idea to have a /, /home, and swap partition. So / has to be on a physical partition, and then /home and swap can be on logical partitions.

I also plan to use my computer to dual boot as there's applications that I need that I'd rather use on Windows XP (Visual Studio .NET 2008).

AMD64 FX55
1 GB RAM
250GB SATA HD (7,200 RPM)
74GB SATA HD (10,000 RPM)

So, here's the problem (or perhaps confusion is the better word) ... From my understanding it's best to put your operating system and applications that you use the most on the faster hard drive, in my case the WD Raptor 10k RPM. So I'm *thinking* about splitting my 74GB HD into at least 2 physical partitions (Windows XP and Ubuntu) and 1 logical partition (swap.) Meanwhile I was thinking about using the 250GB HD for all my file storage and wanted to span logical partitions from it's parent partition.

I hope I'm not misunderstanding Physical and Logical partitions. Correct me if I'm wrong (PLEASE!) but a Logical partition is just an extension of a Physical partition?

So here's the setup I'm looking for:

WD 74GB HD:
     24GB Physical Partition - Windows XP
     24GB Physical Partition - Ubuntu
       2GB Logical Partition - swap

Maxtor 250GB HD:
     100GB Logical Partition - Windows XP
     100GB Logical Partition - Ubuntu

I left room on both partitions so that I could always install another OS (I want to play around with Kubuntu to try KDE as this is my first time messing with Linux).

Is there any recomendations you can give me to set this up differently? I hope that I have not missed any threads on the forum that have already covered this, I know it can be a pain to see new topics that have already been covered. If there is one out there that I've missed, can you post a link to it and I'll apologize and mark the thread as "Resolved."

Thank you so much in advance!


EDIT: Forgot to mention that / and /home will be ext3 partitions and Windows will be NTFS. Also the title says "3 partitions" because I'm only installing /, /home, and swap right now. I'll install Windows XP later. I'll make sure to read the information about fixing GRUB as I know Windows will break it if I install AFTER Ubuntu.

---

### Post by Moop on 2008-02-09
What you call a physical partition I would call a primary partition. You can only have four primary partitions on each hard drive. So with two hard drives you could have eight primary partitions if you wanted to. 

A logical partition is a partition inside of a extended partition. You can have one or more logical partitions in a single extended partition. 

I'm not sure about Ubuntu but XP runs fine from a logical partition.

---

### Post by merlockmagus on 2008-02-09
you can boot fine from either kind of partition; it's all in the boot manager that handles which partition to boot from, whether primary or logical. The boot manager is installed in the Master Boot Record, or MBR, of your hard drive, and basically manages everything from there.

---

### Post by Ringo1508 on 2008-02-09
Sorry, I meant "primary" partition. So my question is, will I have to make /home a primary partition on the 250GB HD? I just figure i can use the 250GB to store all my data and run applications off of the FASTER hard drive so that I can get better performance. It's remarkable how much faster the 10k RPM drive is compared to slower ones. I noticed the difference when I installed Win XP on both drives (not at the same time, when I was changing things around) and it took forever for it to finish on the 250GB drive.

Anyways ... not sure about the Ubuntu and putting /home on the larger drive and if it can be Logical or not.

---

### Post by Moop on 2008-02-09
I'm not sure what your asking but /home doesn't have to be a primary partition, it can be either kind. I don't think there would be any advantage to having /home on the faster hard drive. (if that's what you were asking. 

You can put  /home on a different hard drive than / if you wanted to. I also have a couple raptors and I do notice a difference with XP mostly in boot speed. I don't see any difference running Ubuntu on a 10k hdd or a 7200 IDE. But that's just me. :guitar:

---

### Post by Shazaam on 2008-02-09
AFAIK you can't have two drives running one partition unless you have a Raid setup.
There are a number of ways to go about doing what you want. Separate /home partitions; a shared Data partition, etc. All have their advantages/disadvantages.

If you are going to install other flavors of linux later you might try this--

74gig use ALL of it for Windows (runs better that way).

250 gig make three partitions=
 a. a 1gig /swap partition
 b. a 100 gig shared multimedia (music, pics, etc) partition (Fat32 or NTFS, read/writable in linux/Windows)
 c. make the rest an Extended partition
Inside the Extended partition chop it up into however many logical partitions you want and when you install the different flavors of linux inside the extended partition have them share the /swap partition already there. Just make sure you install Windows first to the 74gig drive.

My setup (slightly different than above because I don't use XP much)=

80gig WD PATA with Windows XP

320gig WD SATA with-

sda1-Extended partition
Inside extended=
sda5-/swap
sda6-PuppyLinux
sda7-Mepis
sda8-Ubuntu Dapper
sda9-Ubuntu Gutsy

---

### Post by Ringo1508 on 2008-02-09
> **merlockmagus said:**
> you can boot fine from either kind of partition; it's all in the boot manager that handles which partition to boot from, whether primary or logical. The boot manager is installed in the Master Boot Record, or MBR, of your hard drive, and basically manages everything from there.

So when installing Ubuntu I can basically set it up like this then?:

250GB HD:
Partition Type: Logical  ... Mount: /home ... File Type: ext3

74GB HD:
Partition Type: Primary ... Mount: / ... File Type: ext3
Partition Type: Logical ... Mount: swap ... File Type: swap



The Window's installation will come later. Just want to make sure these setting are correct when I go into the "Manual Partition" step of Ubuntu installation.

---

### Post by Ringo1508 on 2008-02-09
> **Shazaam said:**
> AFAIK you can't have two drives running one partition unless you have a Raid setup.
There are a number of ways to go about doing what you want. Separate /home partitions; a shared Data partition, etc. All have their advantages/disadvantages.

If you are going to install other flavors of linux later you might try this--

74gig use ALL of it for Windows (runs better that way).

250 gig make three partitions=
 a. a 1gig /swap partition
 b. a 100 gig shared multimedia (music, pics, etc) partition (Fat32 or NTFS, read/writable in linux/Windows)
 c. make the rest an Extended partition
Inside the Extended partition chop it up into however many logical partitions you want and when you install the different flavors of linux inside the extended partition have them share the /swap partition already there. Just make sure you install Windows first to the 74gig drive.

My setup (slightly different than above because I don't use XP much)=

80gig WD PATA with Windows XP

320gig WD SATA with-

sda1-Extended partition
Inside extended=
sda5-/swap
sda6-PuppyLinux
sda7-Mepis
sda8-Ubuntu Dapper
sda9-Ubuntu Gutsy

I thought you could only boot from Primary partitions though? So if you set up the 3 partitions on the 250GB drive, wouldnt the last one have to be a Primary instead of an extended?

---

### Post by Moop on 2008-02-09
Yes that would work. Swap will hardly ever get used if you want to move it to the other drive.

---

### Post by Shazaam on 2008-02-09
My fdisk---
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38626   310263313+   5  Extended
/dev/sda5               1         781     6273319+  82  Linux swap / Solaris
/dev/sda6             782        3350    20635461   83  Linux
/dev/sda7            3351        8471    41134401   83  Linux
/dev/sda8            8472       26554   145251666   83  Linux
/dev/sda9   *       26555       38626    96968308+  83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders:
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

```

Yes I know my swap size is overkill but I haven't gotten around to resizing it.:)
I have the SATA set up as first boot device in my bios.

---

### Post by Ringo1508 on 2008-02-09
How do you make "Extended" partitions? I'm using the Ubuntu CD to do all of this, and in the Manual Partition phase of the Installation program, it only allows you to "Create New Partition" and then select either "Primary" or "Logical"

---

### Post by Shazaam on 2008-02-09
You need something like a Gparted Livecd and use it to manually set up your partitions (extended, logical) that way first. You can't do that with the Ubuntu livecd.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

