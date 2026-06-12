---
title: "Are there any applications that"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Ob1 on 2006-04-13
give you NTFS write & execute support?

because there is this full portable usd hard drive and i don't have any other hard drive to back it's files up, while i reformat it to FAT32.

---

### Post by nalmeth on 2006-04-13
Basically no. Not safely.
FAT32 is fully read/writable, if reinstalling windows is an option.

---

### Post by aysiu on 2006-04-13
Yes, but they're not 100% reliable yet.

Find a way to back up. Borrow a friend's iPod. Get 100 floppy disks. Burn 10 CDs. Find a way to back up.

---

### Post by Ob1 on 2006-04-13
[QUOTE=aysiu]Yes, but they're not 100% reliable yet.

Find a way to back up. Borrow a friend's iPod. Get 100 floppy disks. Burn 10 CDs. Find a way to back up.[/QUOTE]

well i have a portable media player but unfortunately it's NTFS as well

---

### Post by taurus on 2006-04-13
In other words, if you really want to write to NTFS from Linux, you can BUT you are asking for big trouble with a capital T!!!  It's better to find another way though...

---

### Post by aysiu on 2006-04-13
[QUOTE=Ob1]well i have a portable media player but unfortunately it's NTFS as well[/QUOTE] Do you not have a Windows partition?

---

### Post by Ob1 on 2006-04-13
no i went 100% ubuntu. and this file system problem is not the only problem i face. 

Well i guess i can copy the most important files to my main hard drive and delete the other things.

btw how do i reformat it to FAT32?

---

### Post by aysiu on 2006-04-13
[QUOTE=Ob1]no i went 100% ubuntu. and this file system problem is not the only problem i face. 

Well i guess i can copy the most important files to my main hard drive and delete the other things.

btw how do i reformat it to FAT32?[/QUOTE] Yes, I'd mount the drive using one of these two tutorials:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

Then copy of your important files to Ubuntu. Once that's done ```
sudo apt-get update
sudo apt-get install gparted ntfsprogs
sudo gparted
``` Formatting from that point on should be pretty easy to figure out. Post here if you have GParted questions, though.

---

### Post by Ob1 on 2006-04-13
One problem

when i was going to edit this file "/etc/fstab" my portable hard drive was not listed, and yes it is mounted.

---

### Post by aysiu on 2006-04-13
[QUOTE=Ob1]One problem

when i was going to edit this file "/etc/fstab" my portable hard drive was not listed, and yes it is mounted.[/QUOTE] That's because mount points for portable hard drives are dynamically created--they're not in the /etc/fstab.

Just create a mount point and a line in the /etc/fstab for it.

---

### Post by Ob1 on 2006-04-13
what?, Not a problem, but when i converted it to FAT32 it went from 186 Gb to 190 Gb, according to gparted.

---

### Post by brim4brim on 2006-04-13
Yeah NTFS reduces your space as it uses extra information for security settings etc.. (if I remember correctly) so less of your HDD space goes on these settings giving the illusion of more space when in reality it was always that size but some of it was used for security settings etc...

---

### Post by Ob1 on 2006-04-13
i see, but isin't 4 GB to much?

---

