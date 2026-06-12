---
title: "G4L\G4U for PPC Linux"
date: 2010-01-23
forum: Apple Hardware Users
---

### Post by jfmanamtr on 2010-01-23
I use G4U to clone all the other PCs in the house off on my FTP server. But that disk doesn't seem to like my iBook (probably cause it is i386-based dick). So I was wondering if there was a software\livecd like Ghost 4 Unix, Ghost 4 Linux or Clonezilla for a Linux PPC computer?

~John

---

### Post by linuxopjemac on 2010-01-23
> I have solved with a brutal dd if=/dev/hda of=diskimage on the original
disk mounted on an intel pc ( note: the mac was running linux ), then i
have inserted the bigger one always on the pc, and dd if=diskimage
of=/dev/hda .

Next i have physically mounted the "big" disk on the imac, installed and
launched gparted and created a new partition on the unused space.

[http://sourceforge.net/mailarchive/forum.php?thread_name=49BB8B2A.9030109%40email.it&forum_name=clonezilla-user](http://sourceforge.net/mailarchive/forum.php?thread_name=49BB8B2A.9030109%40email.it&forum_name=clonezilla-user)

---

### Post by jfmanamtr on 2010-01-23
Ok. so what I need to do is take the apple HD & put it into another intel based pc?

~John

---

### Post by tgalati4 on 2010-01-23
You might try booting into "target mode" by holding down the "t" key during power-on until you see a file-folder icon.  This allows your mac to act as an expensive firewire drive.  Connect with firewire to another mac then you can use disk utilities to partition it, repair it, etc.

---

