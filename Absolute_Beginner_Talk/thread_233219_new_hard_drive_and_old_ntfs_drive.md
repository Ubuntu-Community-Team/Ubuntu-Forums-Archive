---
title: "new hard drive and old ntfs drive"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by mapleshade on 2006-08-09
I just installed Dapper-LAMP Server on my old computer: Asus A7N8X mobo, AMD Athlon 2500+, 1 GB ram, 100 GB WD PATA hard drive.  I have a bunch of my DVDs on a ntfs formated WD 320 GB SATA drive.  I just bought a 500 GB Maxtor SATA drive to transfer the movies to.

I want to format the 500 GB with XFS and transfer the movies to it, then reformat the 320 GB with XFS.  I can see the 320 in Gparted and the terminal with ```
sudo fdisk -l
```, but if I double click on it in the Gnome GUI it says Unable to mount the selected volume.  Error device /dev/sda1 is not removable.  Error could not execute pmount.  I also can't seem to find the 500 GB drive anywhere.

Advice appreciated.  Total noob.

---

### Post by Rumor on 2006-08-09
I would try the gparted live CD if I were you. It is available here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It won't mount your drives, but it should show both of them in the drive selection menu and allow you to partition and format them both the way you wish.

Should, being the operative word here :)

---

### Post by crispy_420 on 2006-08-09
By DVDs do you mean ISO images or some other fornat(avi, mpeg, etc.). The real problem you may come across is the issues of linux and NTFS. There are programs out the to read (that are beta) and ones to write (very early beta - I think one was called fuse, maybe). But they all come with a major warning which comes to it may or may not work, but either way you may suffer a total loss. My suggestion is hook up to a Windows computer and backup onto optical disc(if dvd) or a drive formatted as FAT32 (if avi/divx, that whole 4GB limit).

Then again there may be other options. Some of the newer live CDs have some NTFS support. One of which is Knoppix I believe. Here is some info on that and a download link:

[HERE]("http://distrowatch.com/?newsid=03488#0")

I would suggest this distro since it has become a popular one so maybe more users have experienced the same issue and can help you out.

---

### Post by The Noble on 2006-08-10
Wow guys, there is a new ntfs reader and writer recently released which has vastly improved speeds with reading and writing, and better support. It may not be as safe as making a fat32 partition and slowly moving things over, but it should be fairly safe. I have heard of people copying 700 meg avi files over and over again on ntfs (from linux) with no effects, so things should be safe. Let me look for a moment to find the how-to for ubuntu. Several live cd's are now offering this new method from the get-go, like knoppix, and have been safely implimented.

Good luck!

Here is the how-to.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by mapleshade on 2006-08-10
> **crispy_420 said:**
> By DVDs do you mean ISO images or some other fornat(avi, mpeg, etc.). The real problem you may come across is the issues of linux and NTFS.

The DVDs were ripped to VOB files.  
I was under the impression that I would be able to read NTFS, but not write.  If I can format and mount the 500 GB drive in the Ubuntu machine, perhaps I could put the 320 GB drive in a networked Windows machine and transfer the files over the network.

I guess my first task is getting the 500 GB drive installed.

BTW, love the avitar.

---

### Post by mapleshade on 2006-08-10
> **Rumor said:**
> I would try the gparted live CD if I were you. It is available here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It won't mount your drives, but it should show both of them in the drive selection menu and allow you to partition and format them both the way you wish.

Should, being the operative word here :)

I tried the Gparted live disc.  It's showing the same as Gparted in Ubuntu.  I can see the 100 GB system disc and the 320 GB SATA, but no 500 GB SATA.  Both the 320 and 500 SATA show up at boot, so they're recognized by the BIOS.  

There must be something I'm missing.  How do I install (format/partition) a new SATA drive?  Or at least, how do I find it?

---

