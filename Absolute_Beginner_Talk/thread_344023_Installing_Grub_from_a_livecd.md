---
title: "Installing Grub from a livecd?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2007-01-22
I botched up my Linux partition, need to get back into windows but grub is giving error 17. How do I re-install grub to boot windows which is on C:? (hda1). I cannot restore the MBR with the windows disk (it just reboot, everytime).

---

### Post by xpod on 2007-01-22
Mabey this might help

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=install+grub+from+live+cd](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=install+grub+from+live+cd)

EDIT: if you just need to get back into Windows "fixmbr" from the recovery console of a XP cd will do it or a bootdisk with "fdisk" on it will do the same job with "fdisk /mbr"

---

### Post by lyceum on 2007-01-22
If this is too much, the one time I got error 17 I re-loaded Ubuntu and that created the new boot loader, but you loose the old Ubuntu.

---

### Post by Rackerz on 2007-01-22
Cheers, giving it a go now ;).

---

### Post by Rackerz on 2007-01-22
I'm having a lot of problems.

> 
grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,2)

Error 22: No such partition

grub> root (hd0,1)

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> root (hd0,2)

Error 22: No such partition


Surely there is still an MBR that grub can install too?

---

### Post by xpod on 2007-01-22
I`m afraid pointing you to a link was about as much help as i can give you with such matters but if you reckon you`ve made such a complete mess then mabey lyceum`s suggestion might be better.

Start afresh.
Of course finding solutions to problems is always the sensible way to do things but sometimes just throwing that cd back in and waiting the 20 mintues or so for a fresh install is also one of the sensible ways.

It would have been up & running by now:biggrin: 
Sorry i cant tell you more.Someone else will surely

---

### Post by Rackerz on 2007-01-22
Thanks, I'm searching for some alternatives right now :).

---

