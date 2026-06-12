---
title: "Quick question about mount points..."
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by ZeusABJ on 2006-06-21
Just to make sure I'm clear, on a few things when I partition my disks I get several options for "mount points" like the ones listed below:

/
swap
/home
/boot
/usr
/var
/opt

Could someone please explain the significance or define what each of these mount points are and why I'd want to put them on an individual partition? I *think* I'm clear on the first three, but the last three have me scratching my head. Like what does "/var" do for me?

---

### Post by olsonar on 2006-06-21
as I understand it:

/  - root , everything here by default
swap - swap  (virtual memory) - give it about 1GB, unless you have a lot (1GB+) of RAM, then not nessescary
/home - home , user data and settings - advantage of separate: no loss of user data on OS reinstall
/boot - boot files (grub)
/usr 
/var - variable files, logs, temp, etc. - advantage of separate: files are less fregmented = faster performance
/opt

see [http://en.wikipedia.org/wiki/FHS]("http://en.wikipedia.org/wiki/FHS") for more info on the unix/linux filesytem layout

---

### Post by ZeusABJ on 2006-06-22
[QUOTE=olsonar]as I understand it:

/  - root , everything here by default
swap - swap  (virtual memory) - give it about 1GB, unless you have a lot (1GB+) of RAM, then not nessescary
/home - home , user data and settings - advantage of separate: no loss of user data on OS reinstall
/boot - boot files (grub)
/usr 
/var - variable files, logs, temp, etc. - advantage of separate: files are less fregmented = faster performance
/opt

see [http://en.wikipedia.org/wiki/FHS]("http://en.wikipedia.org/wiki/FHS") for more info on the unix/linux filesytem layout[/QUOTE]

Thanks that does clear things up tremendously.

---

### Post by tonyr on 2006-06-22
/usr - a lot of stuff goes here, X11R6, libraries, doc (man), etc.  This is actually the majority
of the space occupied by the original installation.

/opt - a conventional place for optional application packages.  Many 'third parties'
use this as a default installaion point.  If you get a lot of stuff from outside the
Ubuntu/Debian world, you might want to consider a separate partition here.

---

### Post by aysiu on 2006-06-22
I wouldn't recommend creating separate partitions for anything except /home if you're using Ubuntu as a desktop (not server) computer.

---

### Post by ZeusABJ on 2006-06-22
[QUOTE=aysiu]I wouldn't recommend creating separate partitions for anything except /home if you're using Ubuntu as a desktop (not server) computer.[/QUOTE]

Well I have three machines total. One desktop running Windows, one desktop running Ubuntu and the third I plan to make into a file server also running Ubuntu. The server will have four 300GB SATA drives that I hope to run as a RAID 5 array. However I'm learning that Linux RAID support is spotty at best. I found this great guide:

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

The guide shows how to install dmraid under Ubuntu and it works, but it can be a bit spotty. I understand that the latest Linux kernel (v2.6.17.1) adds a great deal of stability to dmraid, so I was hoping that upgrading Ubuntu to 2.6.17.1 would be a relatively easy task. How involved is it to update your kernel?

---

