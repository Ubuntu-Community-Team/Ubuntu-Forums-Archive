---
title: "Dual Boot XP w/ windows bootloader- blank screen?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by zmike1 on 2007-05-06
I'm trying to dual boot through windows, following the procedue described in:

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

Everything seems good until I boot.  Windows is OK, but if I select Ubuntu for booting, all I get is black screen with a flashing cursor.

Does it matter that I'm using Feisty instead?  

when I use this command "dd if=/dev/hda2 of=/mnt/osshare/ubuntu.bin bs=512 count=1" 
(with appropriate changes for my partitioning schema)
I do find that there is a ubuntu.bin file in the shared partition.

It is easy enough to copy into the boot.ini file   unfortunately, it doesn't seem to do anything once it's there.

Is there a way to troubleshoot this, e.g., to see if the ubuntu.bin file is corrupt?

One "How To" siad the file should be called ubuntu.img instead of ubuntu.bin ... might that matter?

---

### Post by zvacet on 2007-05-06
[http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso")

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Nekiruhs on 2007-05-06
Any particular reason you're using the windows bootloader? I sue Grub to start windows its much easier that way.

---

### Post by zmike1 on 2007-05-07
I'm trying to use windows bootloader to preserve the MBR.  If I just go with the default insall, Grub replaces the MBR and then the "Media Direct" functionality doesn't work.    Trying to keep other users on the computer happy.

---

### Post by Cypher on 2007-05-07
In addition to making the changes in boot.ini, you did copy the ubuntu.bin file to C:\, right?

---

### Post by zmike1 on 2007-05-07
Yes.  I did copy the ubuntu.bin file to c:\   
I did the copy in windows, if it matters.

---

### Post by Cypher on 2007-05-07
Hmm..nope, that's the right way of doing it. Now when you did install GRUB, you installed it to the Linux partition itself??

---

### Post by zmike1 on 2007-05-07
Yes.  On the last screen of the install, I clicked the "advanced" tab and it asked where to install.  I typed in (hd0,3) since I my HD is formatted with
FAT16 primary, (Media Direct?)
NTFS primary,  (Win XP)
Extended with:
   FAT 32 (for sharing)
   EXT3  (for Ubuntu)
   Swap (for mysterious things)

FAT32 primary (Windows restore partition)

I *think* that means that grub should go on (hd0,3) the fourth partition...

---

