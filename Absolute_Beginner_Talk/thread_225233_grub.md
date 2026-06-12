---
title: "grub?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by heathen on 2006-07-29
I need to reinstall windows on my laptop (selling it).  The guy buying it doesnt want linux despite how hard I try.  So I tried to put the orginal windows back on.  It's not a "clean" version... it's the ghost image/recovery CD from toshiba..  So, I wiped dapper off and went thru the paces with the recovery CD.. it rebooted and i got:

```
Grub loading 1.5

Grub loading
Error 17
```


Help..  I'm currently running off the live CD..

---

### Post by ESPOiG on 2006-07-29
try using a fresh copy of windows xp if u have or wateva or download gParted Live CD, and format the hdd/s then install and the whole the system should be clean of linux, just make sure u delete all the seperate partitions so it forms the 1 big hdd :P

---

### Post by heathen on 2006-07-29
all i have is my recovery cd and a dapper live CD...  this is currently my only computer..  since im running off live CD it makes it somewhat difficult to burn anything

---

### Post by Pipers_Son on 2006-07-29
Have you tried to reformat the HD? 
Does your recovery CD need an OS on the HD before you can recover?
If the answer is no then try the reformat and then use the recovery CD.

my two cents.

---

### Post by Apple 101 on 2006-07-29
Try to obtain a boot floppy or boot disk of some sort.  Use the command *fdisk /mbr* to repair the MBR.  Another option, if you can get to the Windows Recovery centre is to use *fixboot* and *fixmbr*.

---

### Post by confused57 on 2006-07-29
You could try the Win98SE bootdisk floppy:

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

It's small enough that it might download to memory, & can be installed to a floppy, then bootup & enter:

fdisk /mbr

Procedure is described here under "Uninstall Ubuntu":

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by catlett on 2006-07-29
gag should get you in but without an xp install disc I don't know how you can reload the bootloader. You could always download a copy of XP from a bittorent site and use that to enter the recovery console and run fixmbr.
But for right now GAG should get you in. It is another boot manger. It's a real small download. I find it is easiest to just burn the iso to cd instead of trying to make the boot floppy version. [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by heathen on 2006-07-29
I ended up getting a buddy to give me a cracked copy of pro...  it atleast got me to the point of being able to reload the OEM stuff.. thanks guys..

---

