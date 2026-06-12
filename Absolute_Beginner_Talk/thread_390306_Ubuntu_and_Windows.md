---
title: "Ubuntu and Windows"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-03-21
Hey! I'm new to Ubuntu and have had it installed for a month now and i'm loving it!

I have some software that unfortunately NEEDS to be run on Windows so I was considering creating a 30Gig partition on my 100Gig HD devoted to Windows.

Before I formatted my HD and reinstalled Ubuntu, I had Windows running and decided to create a partition with Ubuntu. What resulted is that I was no longer able to access my Windows and had to format the whole drive...

Essentially, I wanted to ask what the best and safest method to create a dual-boot hard drive would be? I have a copy of partition magic if that helps and I have a copy of MS Windows XP ready to install as well.

Any help would be appreciated :)

Thanks :)

---

### Post by bnl on 2007-03-21
I had Windows already when i decided to install Xubuntu as a dual boot.  The Live CD installed everything seamlessly.  I just had to set which partitions went to Ubuntu and it set up the bootloader.

If you reinstall everything, you might try using partition magic to set up a partition for Windows.  Install Windows on that partition, then use the Live CD to partition out the rest for Ubuntu.  And the installation will take care of the rest.

---

### Post by tonycm1 on 2007-03-21
Thanks for the quick response.

I already have KUbuntu installed and i'm really happy with that. I'm hoping to install a fresh copy of MS Windows on a separate partition and have a dual-boot (KUbuntu/Windows). I just wanted to get some feedback as to what the best procedure would be to a) create this partition, and b) install windows, c) create the dual-boot option :)

Thanks :)

---

### Post by raja on 2007-03-21
If you have an install cd for windows (as opposed to a rescue cd), the best option would be to partition the drive first, install windows and then install Ubuntu. Put Grub on the MBR and then you would be able to dual boot.

---

### Post by mac.ryan on 2007-03-21
> **tonycm1 said:**
> Essentially, I wanted to ask what the best and safest method to create a dual-boot hard drive would be?

My personal preference, assuming you are now with an empty HD (no recoverable installations on it) 
[LIST=1]
[*]Delete all partitions
[*]Allocate the windows partition first (I like gparted from the ubuntu liveCD, but any other programme is fine).
[*]Install Windows **before** you install ubuntu.
[*]Install ubuntu on the empty space of the disk, it will recognise the existence of windows and will configure GRUB accordingly (this won't be the case if you install windows **after** ubuntu.[/LIST]If you are installing everything from the scratch, you might consider preparing a data partition where you will store your files, making them accessible from both win and linux... If you are doing so, the best place to locate this partition would be between the windows and linux one (so that it remains close to both and the HD makes less work...).

---

### Post by steve.horsley on 2007-03-21
I suggest this:

Get a live CD and use **sudo gparted** to shrink the Ubuntu partition (don't use Partition Magic - it seems to have trouble with Linux filesystems). You may also choose to move the swap partition to keep it next to the Ubuntu partition. 

Install Windows. 

Restore the GRUB bootloader: 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation)

Do a backup first, just in case the worst happens. Good luck.

---

### Post by tonycm1 on 2007-03-21
Couldn't I just install the Windows Partition using FAT32 (if it's possible?)... I was under the impression that FAT32 was fully accessible by both Ubuntu and Windows?

---

### Post by kpkeerthi on 2007-03-21
Yes. You can but the file size limit in FAT32 is only 4 GB. This should not be a problem unless you plan to keep large backup or DVD images.

---

### Post by tonycm1 on 2007-03-21
If I wanted a DATA Partition greater than 4 Gigs (FAT32), then what would I format this partition so that it is accessible by both Ubuntu and Windows?

---

### Post by kpkeerthi on 2007-03-21
Its the **file size **limit in FAT32 that cannot be more than 4Gb not the **partition **size. You can format the partition as ext3 and install [ext3 windows driver]("http://www.fs-driver.org/") so that windows can also read and write to it.

EDIT:
But you cannot install windows onto ext3 (I just read your post again). If you prefer to have a separate partition common to windows and linux then you could consider formatting it to ext3.

---

### Post by mac.ryan on 2007-03-21
> **tonycm1 said:**
> Couldn't I just install the Windows Partition using FAT32 (if it's possible?)... I was under the impression that FAT32 was fully accessible by both Ubuntu and Windows?

Yes, it is, but it is also a file system that has less features and is less performing. Namely it miss [journaling]("http://en.wikipedia.org/wiki/Journaling_file_system"). To keep the story short: it is less safe than both NTFS and EXT3.

> If I wanted a DATA Partition greater than 4 Gigs (FAT32), then what would I format this partition so that it is accessible by both Ubuntu and Windows?The **partition size** can be greater, but the **size of a single file** cannot.

My personal preference would therefore be:[LIST]
[*]windows installation --> NTFS
[*]linux installation --> EXT3
[*]shared data partition --> 3 options:[/LIST][INDENT][LIST=1]
[*]FAT32 and no additional operations (with limitations you know)
[*]EXT3 with EXT3 drivers for windows (safe)
[*]NTFS with NTFS r/w drivers for linux (namely "experimental", but loads of people use it on their desktops...)[/LIST][/INDENT]

---

