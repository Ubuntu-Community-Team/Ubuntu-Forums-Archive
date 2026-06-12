---
title: "ubuntu dual boot with opensuse"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by viperskunk on 2008-04-20
hi 
i am an ubuntu user, but have been using it for only the last couple of months.
i installed opensuse alongside the gutsy i had.
but now, when i start my computer, the opensuse boot screen comes, with ubuntu as an option.
when i sroll down to the ubuntu option, and press enter, it is unable to boot.
i want to re install ubuntu.
however, when at the partition editor, i assign" / " as the mount point of my hard disk partition on which i want ubuntu installed, will it make ubuntu my default boot screen with suse as an option?
i don't want that.
i wan to keep the suse as primary boot option, with ubuntu shown on the boot screen.
how do i install ubuntu fresh, and have this?
please help.
thanks a lot in advance.

---

### Post by quirks on 2008-04-20
> when i sroll down to the ubuntu option, and press enter, it is unable to boot.
What is the error message, when you try to load Ubuntu? Maybe we can fix this. Might be easier than reinstalling Ubuntu.

> i wan to keep the suse as primary boot option, with ubuntu shown on the boot screen.
If you don't mind that Ubuntu might overwrite the SuSE boot loader with its own one, it should be only a matter of configuration. You can define quite easily, what the default boot option should be.

---

### Post by iSplicer on 2008-04-20
Just a simple suggestion if you havent thought about this before, if you are using openSUSE for its KDE desktop environment, you can always install KDE on ubuntu and choose whether you want to use GNOME or KDE. That way you can have all your stuff on one OS, and no hassle with boot loaders.

---

### Post by rudeboyskunk on 2008-04-20
ok, first things first.  boot into opensuse, and then find the file /boot/grub/menu.lst and copy and paste its contents into here.  then we'll figure out what to do.

---

### Post by sandysandy on 2008-04-20
please post output of

[COLOR="Blue"]sudo fdisk -lu
[/COLOR]
and [COLOR="Blue"]post ur menu.lst file[/COLOR] as suggested in post above

do u know which partition u have installed ubuntu and open suse on.

regards

---

### Post by viperskunk on 2008-04-20
my /boot/grub/menu.lst for suse reads:

# Modified by YaST2. Last modification on Sun Apr 20 17:05:22 IST 2008
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,0)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.3 - 2.6.22.17-0.1
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.22.17-0.1-default root=/dev/disk/by-id/scsi-SATA_FUJITSU_MHV2060NWA0T6728BEU-part1 vga=0x314 resume=/dev/sda5 splash=silent showopts
    initrd /boot/initrd-2.6.22.17-0.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.3 - 2.6.22.17-0.1
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.22.17-0.1-default root=/dev/disk/by-id/scsi-SATA_FUJITSU_MHV2060NWA0T6728BEU-part1 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.17-0.1-default

###Don't change this comment - YaST2 identifier: Original name:  Linux Mint, kernel 2.6.22-14-generic (/dev/sda6)###
title Linux Mint, kernel 2.6.22-14-generic (/dev/sda6)
    root (hd0,5)
    configfile /boot/grub/menu.lst



and open suse is installed on a partition something called /dev/sda1
while ubuntu is on /dev/sda6.

and it is fine if i have to do a fresh install, because i want to. i have messes up quite a bit of the ubuntu. 
thanks for the amazingly quick replies guys.

---

### Post by viperskunk on 2008-04-20
and the output of sudo fdisk -lu is:


Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ddaf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    56131109    28065523+  83  Linux
/dev/sda2        56131110   117226304    30547597+   f  W95 Ext'd (LBA)
/dev/sda5        56131236    58637249     1253007   82  Linux swap / Solaris
/dev/sda6        58637313    97707329    19535008+  83  Linux
/dev/sda7        97707393   117226304     9759456    b  W95 FAT32


thanks.

---

### Post by sandysandy on 2008-04-20
do u have linux mint or ubuntu (though mint is of course a derivative of ubuntu)

there is a utility called super grub disk - [COLOR="Blue"]SGD [/COLOR] for short ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/))  or ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/))

u can download it and burn it as iso image. then u can boot from the bootable CD and use the various options which r self explanatory. u can fix MBR of windows XP or Linux etc.

heres a tutorial on Super Grub.

[http://users.bigpond.net.au/hermanzo...bdiskpage.html](http://users.bigpond.net.au/hermanzo...bdiskpage.html)

what u can do is boot in [COLOR="Blue"]SGD[/COLOR] and restore ubuntu's grub.

u can then boot into ubuntu. once in ubuntu u can follow this thread to reload GRUB which should add ur Open Suse to the GRUB as well.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

(u can do similar thing from Open Suse but Ubuntu is better at locating other OS)

take [COLOR="Blue"]backup of menu.lst [/COLOR]as safety

regards

---

### Post by viperskunk on 2008-04-21
thanks.
the site ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) was outdated so i went to the other one and followed the instructions.
it works fine now.
but i have the ubuntu boot loader and i can't seem to be able to change it.
but i guess it is fine.
thanks a lot people. it really helps to have a forum like this!

---

### Post by rudeboyskunk on 2008-04-21
i had this exact same problem last fall when i was dual-booting opensuse and ubuntu.  basically i would just have to install ubuntu first then opensuse in order to have the opensuse splash image come up as the bootloader screen.

---

### Post by bodhi.zazen on 2008-04-21
I wrote a multiboot tutorial here :

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

Just a small pit of advice, if you chainload it may be a little easier to add distros to your grub menu. If you do not chainload, you will need to manually update your menus with each kernel update.

---

