---
title: "Newbie post re: Kubuntu install"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by htuwlugfaD2 on 2007-10-08
I have a 160 GB drive with 2 partions.  60 gigs has a WinXP install and the remainder is also NTFS and is empty.  When attempting to install Kubuntu, I encounter a problem at step 4 (Prepare disk space).  The only option is : Manual.  The next screen, Prepare partitions is empty (I am sure there should be SOMETHING there!).  Unfortunately, after a previous failed Linux install, I seem to be unable to boot into XP as well.  I am a 52 yr. old newbie trying something new and I'm just about ready to give up, wipe the drive and reinstall Windows.  Any help teaching this old dog a new trick would be appreciated.

---

### Post by kellemes on 2007-10-08
You better delete the (remainder) NTFS-partition, this way you can instruct the installer to use the empty space to install itself.. It will make partitions and stuff, all automatically.
After installing Ubuntu.. normally it will see Windows and create an entry for it, if not.. you can fix your bootloader using the Ubuntu LiveCD of [SuperGrubDisk]("http://supergrub.forjamari.linex.org/").

Edit: Like so often.. after you grasp all of this, you'll feel like a puppy again.

---

### Post by htuwlugfaD2 on 2007-10-08
> **kellemes said:**
> You better delete the (remainder) NTFS-partition, this way you can instruct the installer to use the empty space to install itself.. It will make partitions and stuff, all automatically.
After installing Ubuntu.. normally it will see Windows and create an entry for it, if not.. you can fix your bootloader using the Ubuntu LiveCD of [SuperGrubDisk]("http://supergrub.forjamari.linex.org/").

Edit: Like so often.. after you grasp all of this, you'll feel like a puppy again.
I currently have no access to XP to delete the second partition.  Is there another way to do so?

---

### Post by om1 on 2007-10-08
you need to use gpartition it is in one of the menus on the kubuntu live cd... delete the extra NTFS partition and you should be able to use the installer to finish up

---

### Post by htuwlugfaD2 on 2007-10-08
> **om1 said:**
> you need to use gpartition it is in one of the menus on the kubuntu live cd... delete the extra NTFS partition and you should be able to use the installer to finish up
I guess I must be older than I thought as I can't find that program anywhere.  Looked manually, used Search but no luck

I just found a program called qtparted v0.4.5 - cvs which seems to be a partitioning program.  However, it doesn't detect the HDD.  It says:  No device found. Maybe you're not using root user?  Have no idea what that means.

---

### Post by mivo on 2007-10-08
GParted can be found [here]("http://gparted.sourceforge.net/livecd.php"). Burn the Live CD and boot with it, this will allow you to format and partition the disk. Make partitions for Windows and Linux, and install Windows first, then Ubuntu. :)

---

### Post by om1 on 2007-10-08
click the k then system >> Partition Editor

---

### Post by htuwlugfaD2 on 2007-10-08
> **htuwlugfaD2 said:**
> I guess I must be older than I thought as I can't find that program anywhere.  Looked manually, used Search but no luck

I just found a program called qtparted v0.4.5 - cvs which seems to be a partitioning program.  However, it doesn't detect the HDD.  It says:  No device found. Maybe you're not using root user?  Have no idea what that means.
I have managed to install Kubuntu without losing my XP install.  I want to thank everyone for their assistance in this, especially"mivo" for the GParted link.  Hopefully this old dog can learn how to use it.  It's good to know that there are helpful forum posters out there to make my life easier.  Thanks again.

---

