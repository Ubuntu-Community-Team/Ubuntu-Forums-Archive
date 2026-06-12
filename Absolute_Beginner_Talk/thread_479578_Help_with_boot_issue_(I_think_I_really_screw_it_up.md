---
title: "Help with boot issue (I think I really screw it up)"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by racso39 on 2007-06-20
facts:

1 HD, 4 partitions

2 partitions are NTFS (one for windows, one for files)
Other 2 are Swap and Linux Ubuntu

So I wanted to delete Ubuntu and restore those 2 partition and merge it again with Windows partition.

I boot windows and used partition magic 8.0 to format Linux and Swap partition, conservating their original file system, I just clean it up, now when I boot, I get this:

GRUB Loading stage1.5.

Grub loading, please wait...
Error 15

_


I need help to boot windows again. AND GET MY FILES BACK :(

---

### Post by racso39 on 2007-06-20
Help me, is really an emergency, I need to use my computer.

---

### Post by wonk-o-matic on 2007-06-20
Hi, racso39.

I'm not sure I understand, but you can clarify things if my answer does not fit your situation.  

If you deleted the Ubuntu partition, then you also deleted the /boot directory that GRUB was pointing to.  So, you could use your Windows disk to reinstall the Windows boot manager.  (I think you run FIXMBR.)  

If you had advanced knowledge, you could boot from a live Linux CD and patch things up, but that is not the Absolute Beginner way.

---

### Post by racso39 on 2007-06-20
I ran Linux Live CD and saw that my files are still there in sda1, should I just install Linux again in the partition where it was?

BTW, I didnt delete the partition, I just format it, not the windows one, both swap and Linux.

---

### Post by racso39 on 2007-06-20
As I am speaking (writing) I managed to type fixmbr on repeair console of windows (is SATA RAID disk so I had to use my floppy disk) abd got my windows back, thanks!!!

Now please tell me the safest way to delete both Linux and Swap partition and merge it again with the partition where my windows installation is, using partition magic 8.0.

Sorry I was in panic mode.


EDIT: Nevermind, I figure it out already, thanks.

---

