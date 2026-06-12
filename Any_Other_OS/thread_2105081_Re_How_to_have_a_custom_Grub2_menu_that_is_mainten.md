---
title: "Re: How to have a custom Grub2 menu that is maintenance free"
date: 2013-01-14
forum: Any Other OS
---

### Post by ChinaJustin on 2013-01-14
Just did a clean install of Linux Mint Nadia (based on Ubuntu 12.10) and tried setting up my Grub 2.00 menu as normal. But ran into two problems:

1) When I run 'update-grub', I do not get the echo line from my 06_custom file. Also related to this problem is that my Grub menu items are the standard ones, and **not** the labels I wanted (i.e. "Windows Vista (/bootloader) on sdax" as opposed to just "Windows Vista").
2) When I **chmod -x** the os_prober file and run **update-grub**, it only "finds" my Vista partition. Now, I only have the kernel that came installed with LM 14, but I don't remember my only having one installed kernel being an issue before; as I recall, even with just one kernel it recognized and added the appropriate entry to the Grub menu. But now, if I run **ubdate-grub** and reboot, I just see my Vista partition.

Here is my 06_custom file:

```
#!/bin/sh
echo 1>&2 "Adding Linux Mint and Windows Vista"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above. 
menuentry "Linux Mint 14 - Nadia" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
menuentry "Linux Mint 14 - Nadia (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}
menuentry "Windows Vista" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32C2B4EDC2B4B707
    chainloader +1
}
```

Ideas?

---

### Post by howefield on 2013-01-15
Thread moved to the "*Other OS/Distro Talk*" forum.

Linux Mint support forums : [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by sudodus on 2013-01-15
Cut and paste and modify from an entry that works in [FONT="Courier New"][SIZE="3"]/boot/grub/grub.cfg[/SIZE][/FONT]. It might be better to use the UUID of the partition to be sure to point to the correct one.

For example:

```
menuentry "Ubuntu, with Linux 3.2.0-33-generic (on /dev/sdb2 usb3-os)" --class gnu-linux --class gnu --class os {
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos2)'
        search --no-floppy --fs-uuid --set=root 3857acab-cc88-44a0-af4f-c37b3247fe50
        linux /boot/vmlinuz-3.2.0-33-generic root=UUID=3857acab-cc88-44a0-af4f-c37b3247fe50 ro vga=785
        initrd /boot/initrd.img-3.2.0-33-generic
}

```

---

