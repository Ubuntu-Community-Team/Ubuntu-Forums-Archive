---
title: "Frigging Ubuntu S.O.S!"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Archoniam on 2007-08-02
My ubuntu has turned into an evil frigging devil.It plays keep-away with my Ubuntu CD-ROM. It makes files have errors foaming out their mouth. It refuses to rename my drive in terminal or graphically. The frigging fawn is making ME feisty!

Errors are:
Tried to rename my drive: 
archoniam@claptop:~$ sudo e2label /dev/sdb1/ ldrive
e2label: Not a directory while trying to open /dev/sdb1/
Couldn't find valid filesystem superblock.
archoniam@claptop:~$ 

Tried to install Syslinux:

(Must be explained)
i apt-get installed syslinux. Tried to mount my CDR. It mounted for .2 seconds and then UNMOUNTS ON PURPOSE and says i need the disk.

I am in a FLASH DRIVE NIGHTMARE! 

And last of all...

[SIZE="7"]HELP!SOS!OMGLOL![/SIZE]

---

### Post by asmoore82 on 2007-08-02
[SIZE="5"]"/dev/sdb1/" ==> "/dev/sdb1"[/SIZE]
:KS

---

### Post by thefoolisme on 2007-08-02
> **asmoore82 said:**
> [SIZE="5"]"/dev/sdb1/" ==> "/dev/sdb1"[/SIZE]
:KS

Took me a minute...yeah, that would be an easy mistake.

---

