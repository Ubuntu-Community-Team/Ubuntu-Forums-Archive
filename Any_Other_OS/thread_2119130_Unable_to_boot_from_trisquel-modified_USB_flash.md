---
title: "Unable to boot from trisquel-modified USB flash"
date: 2013-02-23
forum: Any Other OS
---

### Post by netboy123 on 2013-02-23
Hello,

I have used the method in the following url to create a trisquel-modified.iso.
[http://www.trisquel.info/en/wiki/customizing-trisquel-iso](http://www.trisquel.info/en/wiki/customizing-trisquel-iso)

I wrote trisquel-modified.iso in a cdrom and it boots fine without any problems.

Then I used my usb stick and did the following. (The usb stick was having one FAT32 partition).
dd if=trisquel-modified.iso of=/dev/sdb1

It wrote the contents of trisquel-modified.iso to sdb1. Then I tried booting from the usb stick, but it never boot. It is just showing the screen "Loading the Operating System..." and it stays there.


Please help me to know, what is wrong here. My intention is to boot trisquel-modified.iso from a usb stick that is having iso9660 filesystem.


Thanks.

---

### Post by kiyop on 2013-02-23
I do not know trisquel-modified.iso at all.

But I know dding to partition (/dev/sdb1 or so) usually fails.

Do not dd to partition, but dd to whole media, in order to boot by using the MBR of the media (where an iso file is dd'ed).

```
dd if=some.iso of=/dev/sdb
```In order to boot from the MBR of /dev/sdb (which is written by dd command), the following is bad:
```
dd if=some.iso of=/dev/sdb1
```

---

### Post by netboy123 on 2013-02-23
> **kiyop said:**
> 

But I know dding to partition (/dev/sdb1 or so) usually fails.

Do not dd to partition, but dd to whole media, in order to boot by using the MBR of the media (where an iso file is dd'ed).

```
dd if=some.iso of=/dev/sdb
```

I did the same.
dd if=trisquel-modified.iso of=/dev/sdb

Now it doesn't detect the usb stick at all. It displays the grub menu from my computer's hard disk instead.

---

### Post by kiyop on 2013-02-23
EDIT AT Sun Feb 24 12:43:49 JST 2013;

**I confirmed that the generated USB flash (dd'ed by [http://mirror.fsf.org/trisquel-images/trisquel-netinst_5.5_i386.iso](http://mirror.fsf.org/trisquel-images/trisquel-netinst_5.5_i386.iso)**[B]) boot successfully and show graphical installer selection menu after I changed BIOS configuration so that PC boots from USB media first.
So, your problem may be due to your wrong configuration.[/B]

If your dd'ed CD boots correctly and if your dd'ed USB flash does not boot correctly, your created trisquel-modified.iso may not have proper initramfs (initrd.img or so) to boot from USB flash.
Are you sure that your PC can boot from USB flash?
Are you sure that your PC tries to boot from USB flash first?
You can check BIOS / EFI configuration.

If your PC can boot from USB flash and your PC tries to boot from USB flash before attempting to boot from the internal HDD,
one possible reason is that the created ISO file lacks the proper modules to recognize USB flash.
Another possible reason is that it lacks the proper commands to boot from USB flash.
> **netboy123 said:**
> I have used the method in the following url to create a trisquel-modified.iso.
[http://www.trisquel.info/en/wiki/customizing-trisquel-iso](http://www.trisquel.info/en/wiki/customizing-trisquel-iso)
You can analyze initramfs file by expanding by the following method.

Mount the created iso file on /mnt.
```
sudo su -
TYPE ROOT PASSWORD IF ASKED
mount -o loop /PATH/TO/trisquel-modified.iso /mnt
```Find initramfs file like "initrd.img" in /mnt.
Create "initramfs" directory and enter into the directory and expand the initramfs file.
```
mkdir initramfs && cd initramfs
gzip -dc /mnt/PATH/TO/INITRAMFS_FILE_NAME |cpio -i
```You can now get expanded initramfs in the directory "initramfs".
You can analyze some script like init in the initramfs directory.
The name of some modules may end with ".ko", although I do not know trisquel at all.
```
find . -iname *.ko
```If you can boot any linux, boot it and connect the USB flash. Run [boot info script]("http://bootinfoscript.sourceforge.net/") and report the contents of the generated RESULTS.txt here between "[ code]" and "[ /code]" tags (remove the spaces just after "[").

If the grub installed onto the MBR of the internal HDD boots at start-up time, you may be able to manually boot into the created USB flash. Find the kernel file and the initramfs file and the boot loader configuration file. Type c key at grub menu, then you can enter into the grub command line.
```
ls
```displays the recognized media. Find the USB flash and partition where the kernel and the initramfs file and the boot loader configuration file. You can even display the contents of the configuration file (text file)
```
cat FILE_NAME
```But be careful. You should add "(hd2,msdos2)/" or so to specify the partition or you should set the partition as root by
```
set root="(hd2,msdos2)"
```before the cat command.
Try boot with
```
linux PARTITION/PATH/TO/KERNEL_FILE_NAME KERNEL_OPTION
initrd PARTITION/PATH/TO/INITRAMFS_FILE_NAME
boot
```I downloded:[B]
File[/B]: trisquel-netinst_5.5_i386.iso[B]
Location[/B]: [http://mirror.fsf.org/trisquel-images](http://mirror.fsf.org/trisquel-images)
and dd'ed to USB flash (/dev/sdc).
```
dd if=trisquel-netinst_5.5_i386.iso of=/dev/sdc
```"fdisk" returns:
> Disk /dev/sdc: 8127 MB, 8127512576 bytes
64 heads, 32 sectors/track, 7751 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x65b553c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          14       14336   17  Hidden HPFS/NTFS
/dev/sdc2              15          20        6144    1  FAT12I am very curious.
/dev/sdc1 has iso9660 file system and contains:
adtxt.cfg     f10.txt  f5.txt  f9.txt         linux     splash.png
boot.cat      f2.txt   f6.txt  initrd.gz     menu.cfg     stdmenu.cfg
exithelp.cfg  f3.txt   f7.txt  isolinux.bin  prompt.cfg  txt.cfg
f1.txt          f4.txt   f8.txt  isolinux.cfg  rqtxt.cfg     vesamenu.c32

Clearly it uses isolinux.
isolinux.cfg enable menu.cfg, which enables stdmenu.cfg, txt.cfg and gtk.cfg.

txt.cfg contains:
> default install
label install
    menu label ^Install
    menu default
    kernel linux
    append vga=788 initrd=initrd.gz -- quiet So, with trisquel-netinst_5.5_i386.iso, if the USB flash is recognized as (hd2), you can boot by
```
set root="(hd2,msdos1)"
linux /linux vga=788 -- quiet
initrd /initrd.gz
boot
```But after reboot, the dd'ed USB flash is recognized as (rd) by grub4dos-0.4.5c and the information on it is:
drive 0x7F(LBA): C/H/S=523/255/63, Sector Count/Size=8388608/512 Filesystem type unknown, using whole disk

I tried with grub4dos-0.4.5c prompt,
```
rootnoverify (rd)
chainloader +1
boot
```But, the above gives:
Error 8: Kernel must be loaded before booting.

I wonder if trisquel-netinst_5.5_i386.iso is not for USB media.
You can contact trisquel developers, or you can ask at trisquel forum: [http://trisquel.info/en/forum](http://trisquel.info/en/forum)

I confirmed that [my tool]("http://kiyoandkei.blog68.fc2.com/blog-entry-52.html") can boot the created USB flash and start installation of trisquel. 
My tool listed /dev/sdc1 and /dev/sdc2. I selected /dev/sdc1.
I manually selected /linux as kernel and initrd.gz as an initramfs file and give the following as kernel option:
vga=788 -- quiet

Then, it successfully started the installation process.

Also I confirmed that grub2 can detect the first and second partitions of the created USB flash recognized as "(hd2)".
I could boot the installer by grub2 (version 1.98) command line:
```
set root="(hd2,msdos1)"
linux /linux
initrd /initrd.gz
boot
```P.S.: With grub2, if I use "vga=788" as kernel option, it returns an error message like:
vga=788 is deprecated. Use ....

P.S.2: I know I should use usual live image iso file instead of netinstaller iso file. But usual live image iso file is large and it takes long time for me to download it.

P.S.3: I think this problem is specific to trisquel. To benefit answerers, I suggest you changing the title of this thread to "Unable to boot from trisquel-modified USB flash"

---

### Post by Plumtreed on 2013-02-24
Thanks Kiyop....very clever....kiyoshi,too!

---

### Post by oldfred on 2013-02-24
Changed title as that suggestion made sense.

Only some ISO can be installed with dd. Ubuntu only updated with 11.10.
       The daily ISOs for the Ubuntu Oneiric 11.10 development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs. dd
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)

Some ISO also can be directly booted by grub2 with loopmount. I use this both from flash drive and hard drive to install Ubuntu. Works with gparted and some others but not sure with tri-squel.

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)
may need this for some 
insmod iso9660
sudo umount -lrf /isodevice

You can check if your version is supported by any of these, as then you will know it will boot with grub2's loopmount.
       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

