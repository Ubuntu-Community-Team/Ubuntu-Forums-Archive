---
title: "Attempting triple boot"
date: 2008-01-22
forum: Apple Intel Users
---

### Post by smocksturr on 2008-01-22
Okay, so right now i have windows and leopard running well on my macbook.  i'd like to throw some ubuntu on there.
tried installing refit but when i try to boot windows i get a GRUB hard disk error.
do i seriously have to install windows AFTER refit?

---

### Post by benanzo on 2008-01-22
From the rEFIt menu you need to choose the partitioner and sync MBR/GPT so the correct partitions are recognized.

---

### Post by smocksturr on 2008-01-22
No dice.
Said that there was no need to sync.
Also, I tried to boot Windows once and it hung.
Tried again and got the GRUB hard disk error.
I don't have my windows install disk but i do have a backed up partition on my external drive for windows.
Should I somehow redo my partition table or something?
I have no idea.
I would rather not reinstall Mac, I lost my Leopard disc.

---

### Post by cyberdork33 on 2008-01-22
If you are getting a GRUB error, then you must have attempted to install Ubuntu (or some other distro) already. This is not the fault of rEFIt. You can boot your windows disc into recovery mode, and fix the MBR... (fixmbr command).

This utility might work too:
[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)
I haven't tried it, but it claims to be able to write a windows bootsector on the disk.

---

### Post by bunted on 2008-01-23
Your problem might be that you have to edit the boot.ini file on your Windows partition.  Likely, when you installed Ubuntu, the hard drive partition changed from when you first installed Windows.  Just open that file with a text editor from a live cd or another working OS on the local drive.

Not sure of your exact install method, but if you need more help, check here:
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp")

---

