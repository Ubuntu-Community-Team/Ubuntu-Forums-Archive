---
title: "Getting to XP from GRUB"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by FreakinSyco on 2007-01-23
I can boot to either XP or Ubuntu by changing the boot order in BIOS. It would be nice if I could just have either Ubuntu or XPs bootloader do the job.

I have 3 HDDs in my computer. 2 x IDE and 1 x SATA. HDA is Ubuntu, HDB is Media Storage and SDA is Windows XP.

I have attempted editing the boot.ini and adding a .bin file thats the first bit of HDA and so on... but that didnt work. I recieve nothing but a flashing "_".

So I'm attempting to configure GRUB. Heres the contents of my fstab and the contents of my menu.lst

[quote=FSTAB]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=985b4ab9-c957-40f3-8486-7be466cb3b46 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=4542-568B  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=385085A550856B08 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=c9493bfa-9e16-45f0-a887-8943dc2081cd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
[/quote]

[quote=Menu.lst]
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader +1
[/quote]

So what am I missing? When I select MS Windows XP from the GRUB menu upon bootup I get an "This drive is not bootable. Please insert bootable floppy disk" or something similar to that.

---

### Post by housam on 2007-01-24
Try to use the super grub disk to fix it .
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by bionnaki on 2007-01-24
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_Windows_entry_into_GRUB_menu)

---

### Post by Canis familiaris on 2007-01-24
Perhaps this link will help:
[http://www.linuxquestions.org/linux/answers/print/441?]("http://www.linuxquestions.org/linux/answers/print/441?://")

---

### Post by FreakinSyco on 2007-01-24
> **Anurag_panda said:**
> Perhaps this link will help:
[http://www.linuxquestions.org/linux/answers/print/441?]("http://www.linuxquestions.org/linux/answers/print/441?://")


I've tried that before, but will try it again when I get home to in case. Any other ideas?

---

