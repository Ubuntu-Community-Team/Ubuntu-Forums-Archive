---
title: "Re-partition?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by drbob07 on 2007-04-07
Alright, I've finally given up using Windows and I am ready to move on.

Or... not quite.

I have 1 hard drive, and I'd like to re-partition it into 2 partitions, so that I can put Ubuntu on 1, and keep Windows on the other.

Are there any free programs that will re-partition a drive (without losing the data), or will I need to go get a new drive to put Ubuntu on. (Or wipe Windows out)

Also, can Ubuntu read NTFS? (Read, not necessarily write)... I have important documents that I don't necessarily want to copy back and forth between the OS'es via USB Thumb-drive... :-/


So, any help would be greatly appreciated.

I guess if worse comes to worse, I can always buy a new hard drive, or back up my Windows partition.

(Thanks in advance )

---

### Post by Bachstelze on 2007-04-07
You can very well resize your NTFS partition without losing any data using GParted (which is on the Ubuntu Live CD, among others). I personnally never had any problems with it but nothing in this world in 100% safe so I strongly recommend you backup all valuable data before proceeding. Also, it is a good idea to defrag your Windows partition before.

Ubuntu (and Linux in general) can read NTFS perfectly and tools exist to enable write access too. Once again, it usually works but is not 100% safe so use at your own risk. I would rather recommend doing it the other way around (i.e. enable read/write access to our Linux partitions in XP, which is considered much more safe, google for 'ext2ifs')

---

### Post by chalex on 2007-04-07
The ubuntu installer can resize your Windows partition and create a new one for Ubuntu in the remaining free space.

Yes, reading an NTFS volume is no problem.

You can also use the GParted LiveCD.

You should make backups in case anything goes wrong.

---

### Post by Gina on 2007-04-07
You can use the Linux Gnome Partition Editor (free) called **gparted **which you can install using an Ubuntu live CD.  Once you've tidied up Windows and used defrag to move all the files to the beginning of the drive, you can use **gparted **to resize the Windows partition without losing Windows or it's data.  Then you can use the freed space to make new partitions for Ubuntu.  Then install Ubuntu - again from the live CD - into the partitions you've just made.  It will detect Windows and create a dual-boot system - so you can boot either into Ubuntu or Windows.

But backup all important data etc. before using the partitioner - things can go wrong.

**Edit... **The 2 posts above were posted as I was writing this :lol:

---

