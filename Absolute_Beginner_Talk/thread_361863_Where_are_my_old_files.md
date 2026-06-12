---
title: "Where are my old files?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Bayushi Red on 2007-02-14
Today I installed Ubuntu 6.10 on a brand new hard drive.  Also in my computer is another drive with all my documents, music, photos, etc. that I still have from my last OS installation, Windows XP.

I've been poking around the file system for the last couple hours, trying to find my old files, to no avail.  The drive is recognized by Ubuntu, and it even knows that it's formatted and what the volume is called.

So where are my files?

Possible complications:
The drive is formatted in NTFS
Did I need to add this drive to the partition list when I installed?  If I did that, would I have lost my files?

Thanks in advance for your help.

---

### Post by meng on 2007-02-14
It's probably under
/media/hda1
(replace hda1 with the device name of the NTFS partition)
Otherwise drop to terminal and type:
sudo fdisk -l (L as in Larry)
to find out which partition it is.

---

### Post by 42Wired on 2007-02-14
Apparently, posts cannot be deleted in this forum...

---

### Post by 42Wired on 2007-02-14
I followed [this]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/") to install Ubuntu next to WinXP, and it says to set up a FAT32 partition for sharing data between Linux and Windows. I just did it and didn't ask questions, but is Linux incompatible with NTFS format?

---

### Post by Bayushi Red on 2007-02-14
Okay, it seems that the drive itself is in the file system.  Ubuntu knows how big it is, all it's salient stats.

But I had numerous files on the hard drive in question, and THOSE are what I can't find.
Is there a way I can view all the files on a given drive?

---

### Post by jimrz on 2007-02-14
> **Bayushi Red said:**
> Okay, it seems that the drive itself is in the file system.  Ubuntu knows how big it is, all it's salient stats.

But I had numerous files on the hard drive in question, and THOSE are what I can't find.
Is there a way I can view all the files on a given drive?

follow [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only") link for instructions on how to mount your other hdd...be sure to read down far enough to get the part which tells how to have the drive mount automajically each time you boot the machine.

---

### Post by Bayushi Red on 2007-02-14
That did it.  Thank you for your help.
Edit:  Okay, one more question:  How do I make it NOT read-only?

---

### Post by jimrz on 2007-02-15
> **Bayushi Red said:**
> That did it.  Thank you for your help.
Edit:  Okay, one more question:  How do I make it NOT read-only?

NTFS does not play well with non-MS OS's, there are some progs available that let you write to NTFS but I understand that they are rather risky and can cause serious damage to your NTFS partition/data. there is a reliable driver for win that allows windows to read/write ext2 or 3 (don't know the name but a quick forum or google search should locate it for you). a truly safe way to share your data between win and ubuntu is to create a FAT32 (read/writable by both) partion and use it to move stuff between the 2 when needed.

---

### Post by nhandler on 2007-02-15
If you read farther on that link posted above, it also says somewhere how to set up an ntfs drive to be read and writable. Yes, writing to an ntfs formated drive is considered risky. However, I do it on my computer, and everything has worked fine. So, you really don't need to worry. Just give it a try.

---

