---
title: "usb boot error"
date: 2010-11-15
forum: Apple Hardware Users
---

### Post by 45xx on 2010-11-15
Hi,
I moved a iso of ubuntu 10.10 to my 4gb usb drive and then moved the boot folder with grub, here i set the files to the 10.10 ubuntu and changed the endings of initrd files to lz. now i tried booting the ubuntu iso via the fake bios. it started and ran codes. until a colored solid bar was in the upper half of my screen. then the bar disappeared again. the last code was:

(14:0028944):fb: conflicting fb nw usage nouveaufb vs EFI VGA - removing generic driver
then i waited about 10min, but nothing happened anymore. so im guessing its something with the graphics, or some sort

Info:
a late 2008, early 2009 macbookpro with reffit.




Here is my grub.cfg:
## grub.cfg pxw 20090909 22:00

menuviewer="text"

timeout=20
default=0

set F1=ctrl-x

set color_normal=yellow/red

menuentry "reboot from grub.cfg fat usb " {
reboot
}
menuentry "use /grub2.cfg" {
 search --set -f /grub2.cfg
 configfile /grub2.cfg
}
menuentry "OSX" {
	search --set -f /usr/standalone/i386/boot.efi
	chainloader /usr/standalone/i386/boot.efi
}
menuentry "A ubuntu-10.10-desktop-amd64.iso " {
 fakebios
 fix_video
 search --set -f /ubuntu-10.10-desktop-amd64.iso
 loopback loop /ubuntu-10.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.10-desktop-amd64.iso noefi
 initrd (loop)/casper/initrd.lz
}
menuentry "B ubuntu-10.10-desktop-amd64.iso fbdev " {
 fakebios
 fix_video
 search --set -f /ubuntu-10.10-desktop-amd64.iso
 loopback loop /ubuntu-10.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.10-desktop-amd64.iso video=efifb fbdev noefi single
 initrd (loop)/casper/initrd.lz
}
menuentry "C ubuntu-10.10-desktop-amd64.iso fbdev persistent" {
 fakebios
 fix_video
 search --set -f /ubuntu-10.10-desktop-amd64.iso
 loopback loop /ubuntu-10.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.10-desktop-amd64.iso persistent video=efifb fbdev noefi
 initrd (loop)/casper/initrd.lz
}
menuentry "D slax iso console" {
	fakebios
	search --set -f /slax-6.1.2.iso
	loopback iso /slax-6.1.2.iso
	linux (iso)/boot/vmlinuz from=/slax-6.1.2.iso  ramdisk_size=6666 root=/dev/ram0 rw 
	initrd (iso)/boot/initrd.lz
}
menuentry "E slax iso console persistent" {
	fakebios
	search --set -f /slax-6.1.2.iso
	loopback iso /slax-6.1.2.iso
	linux (iso)/boot/vmlinuz from=/slax-6.1.2.iso  ramdisk_size=6666 root=/dev/ram0 rw changes=slaxper.dat
	initrd (iso)/boot/initrd.lz
}
menuentry "CD" {
   appleloader CD
}
menuentry "MBR1" {
   appleloader HD
}
menuentry "REBOOT" {
	reboot

---

