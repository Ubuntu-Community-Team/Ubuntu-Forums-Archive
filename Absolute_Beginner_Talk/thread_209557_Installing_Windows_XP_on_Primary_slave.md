---
title: "Installing Windows XP on Primary slave"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2006-07-05
Is it possible to install Wndows XP on Primary slave (second harddisk) Im getting an error that I need a fat/ntfs partition on the primary master which have my Ubuntu installed, for the mbr

---------1st Harddrive----------------
hda1 = /boot - 100mb
hda2 = /linux-swap - 1gig
hda3 = /root - 10gig
hda3 = /home - rest...

--------2nd Harddrive-----------------
40gig - unformatted

if I format "hda1" as a fat/32 partition how will I reinstall Grub after installing Windows or can I just set my /boot as Fat/32?
Also my Windows will recognize hda1 as a 100mb (Local Disk) drive, is it possible not to show it in "My Computer"?

---

### Post by taurus on 2006-07-05
Doesn't matter where you install XP, you will have to reinstall GRUB again because XP will wipe your MBR clean.  And as far I as know, XP always wants to be on the master HD but you can install Ubuntu on any partition you want...

---

### Post by jeffreyvergara.NET on 2006-07-05
what if I make my 2nd Harddrive as Secondary Master... Currently my 2nd Master is my DVDrom, then make it primary slave?

---

### Post by MaximB on 2006-07-05
don't know...try it
but do not be afraid to install winxp mbr on grub
install winxp
after that just run the ubuntu installation disk again and fix the grub
it will reconize your winxp OS and it will dual-boot.

---

### Post by confused57 on 2006-07-05
Here's how I have my system set up:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

I'm not sure if this would be what you want?

---

### Post by jeffreyvergara.NET on 2006-07-05
[QUOTE=confused57]Here's how I have my system set up:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

I'm not sure if this would be what you want?[/QUOTE]

I just figured that out but did the opposite on disabling the HD.

So here's what happened

I have an existing installation of Ubuntu on Hda1(master-harddrive1) but I want to install Windows on Hdb1 (slave-harddrive2) but I don't want to format my Ubuntu installation, and Windows installation cannot install to harddrive2 because its a slave and the master partition format is not fat/ntfs.

So i disable my harddisk1 and make harddisk2 to boot after DVDdrive and floppy. Installed Windows, then run it once then reboot then enable my harddisk1 and make it boot first instead harddisk2. then I edited grub and add Windows on the list.

problem solve.. ^^

---

