---
title: "Partitions - Partition table entries are not in disk order"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-02-15
When I run sudo fdisk -l I see this error at the bottom:

Partition table entries are not in disk order

I searched the forums and it seems that people who have this problem are having trouble booting into either Ubuntu or XP. I am running a dual boot, but I am not having any trouble booting into either.  Do I need to fix this, and if so, how do I fix it?

---

### Post by Patrick K on 2007-02-15
I don't think it is an error. Just a statement of fact. I get the same notice but have no problems booting W98 or Edgy.

---

### Post by igknighted on 2007-02-15
Yeah, what it means usually is that your swap partition is placed last in drive numbers, even though physically on the drive its not last.  It isn't an error, its just informing you.  It's nice to know so you don't accidentally erase a partition and end up borking your disk cause you erased the wrong one.

---

### Post by GVaio on 2007-12-22
I am a noob ... but wanted to share my lessons anyway with this community, since the forum posts have helped me get started with Ubuntu.

There is **HOWEVER** an unfortunate consequence of the "entries are not in disk order", as I found out the LOOONG (and HARD) way.

"sfdisk" (used by Clonezilla) when used to RESTORE a partition table burps if the entries are NOT in order ... at least that's what I think has prevented me from a successful restore with Clonezilla.  I am glad to find this out NOW, before the Clonezilla image of the HDD is ever needed.  

Along the way I also discovered that using thrid-party software (like Acronis True Image) to make a DISK COPY similarly causes problem ... the swap partition (which was contained within an extended partition) ends up in a different place on the copy of the original HDD.  Thus I had to edit "/etc/fstab" on the copy.

I am not quite done yet ... still testing the Clonezilla save/restore features to make sure I end up with a reliable (easily restorable) system.

(The original reason why this DUAL BOOT (WinXP/Ubuntu) system originally created the out-of-order partition table entries is unknown, but it might behoove you to check your system with the "sudo fdisk -l" command ... and if necessary FIX THE ORDER (but be aware that this is NOT trivial and should be attempted only if you are very brave and have a good backup of important data): [http://ubuntuforums.org/showthread.php?t=108649]("http://ubuntuforums.org/showthread.php?t=108649")  (see Post #4))

I will post in that thread if I find anything else of note.

---

