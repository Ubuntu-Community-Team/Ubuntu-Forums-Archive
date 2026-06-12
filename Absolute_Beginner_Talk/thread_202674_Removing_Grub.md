---
title: "Removing Grub"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Peleus on 2006-06-23
Reciently I've removed my linux partition and used a windows recovery disc to install the default software and window's XP on my laptop. However now GRUB dies every time I try and boot up coming up with Error 17. 

Unfortuantely my XP disc is just a cheapo recovery disc instead of a proper one so I can't go into the recovery console and type fixmbr. 

All I have at the moment is the ubuntu install CD, so my question is how can I removing grub from here so I can boot through to XP?

Thanks guys.

---

### Post by xXx 0wn3d xXx on 2006-06-23
[QUOTE=Peleus]Reciently I've removed my linux partition and used a windows recovery disc to install the default software and window's XP on my laptop. However now GRUB dies every time I try and boot up coming up with Error 17. 

Unfortuantely my XP disc is just a cheapo recovery disc instead of a proper one so I can't go into the recovery console and type fixmbr. 

All I have at the moment is the ubuntu install CD, so my question is how can I removing grub from here so I can boot through to XP?

Thanks guys.[/QUOTE]
Read [ This tutorial. ](http://doc.gwos.org/index.php/Restore_Grub) It may not be what you want though. This will re-install grub allowing you to boot into windows. Linux will still be gone however. This tutorial was not written for a dual boot system too, so keep that in mind.

---

### Post by Apple 101 on 2006-06-23
Create a MS-DOS boot disk and boot from it.  When you get to the command prompt, type in: *fdisk /mbr* to recreate the Master Boot Record.  Remember to set the XP partition as Active by typing: *fdisk* and following the prompts.

---

### Post by Kilz on 2006-06-23
[QUOTE=Peleus]Reciently I've removed my linux partition and used a windows recovery disc to install the default software and window's XP on my laptop. However now GRUB dies every time I try and boot up coming up with Error 17. 

Unfortuantely my XP disc is just a cheapo recovery disc instead of a proper one so I can't go into the recovery console and type fixmbr. 

All I have at the moment is the ubuntu install CD, so my question is how can I removing grub from here so I can boot through to XP?

Thanks guys.[/QUOTE]

[Go here]("http://www.bootdisk.com/bootdisk.htm") if you dont have a boot disk, get the windows 98 boot disk, make it in a flopy. Put it in and boot. When you get to the a: prompt type in fdisk /mbr

---

### Post by Peleus on 2006-06-23
Also, its a laptop and I don't have a floppy disc :D

---

### Post by Kilz on 2006-06-23
[QUOTE=Peleus]Also, its a laptop and I don't have a floppy disc :D[/QUOTE]
You may have a problem then.

---

### Post by Apple 101 on 2006-06-23
Well use a CD/DVD burning programme to make a bootable CD with the files on it.  Bootdisk.com or Ultimatebootcd.com should help you.

---

### Post by Peleus on 2006-06-23
Ok guys, I just remembered I had a USB Floppy drive in the back of the cupboard, problem solved!!

Thanks heaps for your help guys appreciate it.

---

