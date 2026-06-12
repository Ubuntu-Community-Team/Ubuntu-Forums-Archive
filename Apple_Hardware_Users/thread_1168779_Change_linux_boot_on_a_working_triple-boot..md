---
title: "Change linux boot on a working triple-boot."
date: 2009-05-24
forum: Apple Hardware Users
---

### Post by vinceshaw on 2009-05-24
Having a “Vista/Ubuntu/Leopard”triple boot system on a MacBook Alu for several months. 
There is only one SATA HD, grub is installed on /boot partition, boot manager is rEfit.
It works fine but one inconvenience, no data share amoung the three Oses. So I decided to make a change like belowing:
(sorry, coould not find a working tab, neither tab nor space key works, have to use the dotted line):

The original scheme is---------the new scheme is

Sda1  efi---------------------------Sda1  efi
Sda2  Leopard-------------------Sda2 Vista ultimate
Sda3  linux /boot----------------Sda3 Fat32-share
Sda4  Vista Ultimate------------Sda4 linux /boot
-----------------------------------------------------------
Sda5 linux /root-----------------Sda5 Leopard		
Sda6 linux /home---------------Sda6 linux /root
Sda7 linux /swap---------------Sda7 linux /home
-------------------------------------Sda8 linux /swap
This arrangement meets mbr requirement of both windows and linux boot, while have one share that three system can see. I backed-up three oses, adjusted partition scheme then cloned os back. I expected more problem from Vista but just three minutes repair and one reboot, it worked. Leopard has no issue at all and boot straightly. But Linux is my headache. The rEfit shows a linux item there but boot to it just hangs on forever.

I boot ubuntu 810 install CD into live session, mount sda4 and sda6 and confirmed that the /boot and /root are right there. Then I edited etc/fstab in /root and /grub/menu.lst in /boot

The edited ones are here
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4 	/boot           ext3    relatime        1       1
/dev/sda6	/               ext3    relatime,errors=remount-ro        1      1
/dev/sda7	/home           ext3    relatime        1      2
/dev/sda8 	none            swap    sw              0       0
/dev/scd0      /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I use /dev/sdx to replace original UUID since I don’t know their new ID. It shoulb be Ok.

The menu.lst is ( I skipped commented lines)

# menu.lst - See: grub(8), info grub, update-grub(8)
default		0
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,3)
kernel		/vmlinuz-2.6.27-11-generic root=/dev/sda6 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.27-11-generic root=/dev/sda6 ro  single
initrd		/initrd.img-2.6.27-11-generic

It simply didn't work. I googled a lot, but no solution yet.

Any suggestion is highly appreciated.
Vince

---

### Post by cyberdork33 on 2009-05-26
Are you using rEFIt?

---

### Post by volanin on 2009-05-26
You have to reinstall GRUB in the new /boot partition. Most of the time, a simple clone of the old partition to the new place will not work. You can do that using the liveCD.

---

### Post by vinceshaw on 2009-05-26
Hi, Volanin: 
Thank you very much for your suggestion! It solved my problem of boot linux immediately after the grub is re-installed, although another problem appeared.

The re-installaion of Grub is a little bit tricky.
I followed this guide [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), but use the last edited method and made my own modification as my grub is not on the mbr of the HD, it is on a partition sda4. I tried very carefully to use root (hd0,3) to make sda4 to receive grub. But the returned results was erro install grub to hd0,3 and grub went to MBR without asking my confirmation, and went on "successfully".

After reboot, there is one extra Linux boot item in rEfit menu: one bootable, one not bootable. Leopard boot is fine, but the mbr dependent Vista lost boot ability: it also boot into linux. I'll find a way to get windows boot back and get rid of the extra non-boot linux item. The rEfit mbr and GPT/mbr table looks normal, Windows is still Windows and active, no wrong items found.

Any way, thanks again for your help, I am not worried about Windows Vista, it is there. I am very experienced at modifying mbr and multi-boot on PC, but for Mac, I need some study. It will not be a big problem for me, as mbr item is just a marker, it does not affect the content on the partition.

Also thanks Cyberdork33 for your attention.

Vince.

---

