---
title: "Quad boot (!) Added Freespire--need GRUB help  (So close!!)"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2006-10-22
I know, I'm probably nuts, but I just added Freespire to my AMD64.

On the first hard drive I have XP, and Ubuntu 64-bit.   On the 2nd, newly installed hard drive, I've got Vista and as of an hour ago, Freespire.

When installing Freespire there's an option to write a new MBR, which I chose to DE-select.  

I think I'm really close on my Ubuntu GRUB menu entry(s), but I'm getting an error message:

> root (hd1,4)
Filesystem type unknown, partition type 0x7
Error 17: Cannot mount selected partition

Here's my GRUB menu.lst:

> #
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb4
[COLOR="Red"]title        Freespire Ver. 1.0.13
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.14-gratis root=/dev/scsi/host1/bus0/target0/lun0/part4 rootdev=0x0303 ramdisk=34624 video=vesafb:nomtrr vga=0x311 splash=silent
initrd        /boot/initrd-2.6.14-gratis.gz
boot[/COLOR]


title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I'm pretty sure the "dev/scsi/host1/bus0/target0/lun0/part4" should be correct--I took that off a Freespire message when it installed.

I'm NOT sure about the "rootdev=0x0303 part" at ALL--I took that off the GRUB entry on my 2nd box (an XP, Ubuntu, Freespire box).  Is that hex that has to match the (hd1,4)?

Can anyone help?

---

### Post by gn2 on 2006-10-22
This might help: [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by wilberfan on 2006-10-22
I've got one of those!   But it's a Help! post all on it's own!  :-O

---

### Post by halitech on 2006-10-22
was the second drive SCSI? cause if not, it's pointing to a SCSI drive and that would give you an error

---

### Post by wilberfan on 2006-10-22
You know, I wondered about that!   It's NOT a SCSI drive--it's an IDE drive...!   But that install message specifically said "scsi", so that's what I included.

I made one change that got me a little furter:   It's the old start-counting-from-zero thing:   It's partition FOUR--which means (dammit) (hd1,_3_)!  That allowed me to get to the Freespire boot screen and progress bar--but it just froze there...

---

### Post by wilberfan on 2006-10-22
Well, it's still freezing...  I removed the quiet splash, and I can see it's saying something about a resume2 parameter.

Oy.

---

