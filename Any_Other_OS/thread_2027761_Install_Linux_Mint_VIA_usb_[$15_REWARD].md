---
title: "Install Linux Mint VIA usb [$15 REWARD]"
date: 2012-07-16
forum: Any Other OS
---

### Post by Tyluur on 2012-07-16
I need someone to guide me with installation of the linux mint distribution of linux. I have a USB that is capable of holding the .iso and I've tried doing it but got stuck severally.

EDIT: 

[B]After getting to the install linux mint screen, I get this error:
[IMG]http://i.imgur.com/NFnl6.png[/IMG]


Computer specs:

CPU Type: AMD-A6-3400M APU with Radeon(tm) HD Graphics[/B] [B]
CPU SPEED: 1.40 GHz
Product Name: Aspire 5560
Manufacturer Name: Acer[/B]

---

### Post by digital_k on 2012-07-16
Have a look at this, it works!  No charge. ;)

[http://www.accella.net/create-a-linux-mint-12-bootable-usb/](http://www.accella.net/create-a-linux-mint-12-bootable-usb/)

---

### Post by pqwoerituytrueiwoq on 2012-07-16
This program will do it for you:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Tyluur on 2012-07-16
I did that prior to making this post . I received this error on the unetbootin:

```

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error 
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```

---

### Post by pqwoerituytrueiwoq on 2012-07-16
check the md5sum of your downloaded iso

---

### Post by Tyluur on 2012-07-16
This is my boot priority order:

> 
[LIST=1]
[*]USB FDD: SMI USB DISK
[*]USB CDROM:
[*]USB HDD:
[*]HDDO: TOSHIBA MK6459GSXP
[*]ATAPI CDROM: HL-DT-STDVDRAM GT32N
[*]Network boot: BRCM MBA Slot 0100 v14.6.9
[/LIST]


---

### Post by Tyluur on 2012-07-16
> **pqwoerituytrueiwoq said:**
> check the md5sum of your downloaded iso

i do not know how to do that,  can you assist me over the phone?

---

### Post by pqwoerituytrueiwoq on 2012-07-17
personally i hate phones

[http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/)
[IMG]http://i.imgur.com/8HVsl.png[/IMG]
if it does not match the sum on the page you downloaded it from your iso is damaged

---

### Post by Tyluur on 2012-07-17
Am I to replace the md5sum with the link you gave me?

---

### Post by pqwoerituytrueiwoq on 2012-07-17
use the program on the page to get a md5sum of your iso file
compare it to the md5sum on the version of mint you downloaded
if it is a match your download was good, if it is not a match your flash drive may have crapped out on you or the data was not written correctly in which case choose teat media from unetbootin

---

### Post by Tyluur on 2012-07-17
> **pqwoerituytrueiwoq said:**
> use the program on the page to get a md5sum of your iso file
compare it to the md5sum on the version of mint you downloaded
if it is a match your download was good, if it is not a match your flash drive may have crapped out on you or the data was not written correctly in which case choose teat media from unetbootin

What is teat media?

---

### Post by pqwoerituytrueiwoq on 2012-07-17
*test media* or *test disk for defects* something along those lines

---

### Post by Tyluur on 2012-07-17
I received this data:

```

C:\Users\Ray\Downloads\md5sums-1.2>md5sums.exe g:\

MD5sums 1.2 freeware for Win9x/ME/NT/2000/XP+
Copyright (C) 2001-2005 Jem Berkes - http://www.pc-tools.net/
Type md5sums.exe -h for help

[Path] / filename                              MD5 sum
-------------------------------------------------------------------------------
[g:\]
ubnkern                                        78022dbf0eeae58505060249b75452e1
ubninit                                        5e1969fb52972276be1e39613be7e354
ubnpathl.txt                                   709997b6fd7cb107485c33b2d4aa00ab
autorun.inf                                    d0d31b91a450e7870b9423558e9b171d
md5sum.txt                                     4d3f71afc0ec94502edfa6db77da88f2
mint4win.exe                                   fc6e1f026f4c26105aaf1757d191eded
ubnfilel.txt                                   6c9d40991c6954e9062277e9c9577237
ldlinux.sys                                    d8b6332f170a4df9ef75022515963d15
syslinux.cfg                                   282280f6542e5383e4f2d318e27c3868
menu.c32                                       73308b382ddddfb212de61895648d765

C:\Users\Ray\Downloads\md5sums-1.2>pause
Press any key to continue . . .
```

When running md5sums.exe g:\ [G being my usb]

---

### Post by pqwoerituytrueiwoq on 2012-07-17
```
md5sums.exe C:\Users\Ray\Downloads\*.iso
```we need the md5sum of the iso file you used when you ran unetbootin
Which version of mint are you trying to install?

---

### Post by Tyluur on 2012-07-17
Okay let me run it and give you my outprinted data. Is there any way we can talk on MSN or gTalk or anything else for faster replys?

---

### Post by pqwoerituytrueiwoq on 2012-07-17
> **Tyluur said:**
> Okay let me run it and give you my outprinted data. Is there any way we can talk on MSN or gTalk or anything else for faster replys?
gtalk i can do, i can send a PM

---

### Post by Tyluur on 2012-07-17
I used the 32 bit download from linux mint and after running md5sums.exe mint.iso (i renamed the long name to mint.iso) I got this.

> [C:\Users\Ray\Downloads\md5sums-1.2\]
mint.iso                                  100% 43ca0be4501b9d1a46fea25ec2cd556e


---

### Post by pqwoerituytrueiwoq on 2012-07-17
your MD5 matches (your download came in correclty)
[http://www.linuxmint.com/edition.php?id=103](http://www.linuxmint.com/edition.php?id=103)
i suggest testing the media/disk from the unetbootin menu

do you know what processor is in your system?
you may end up preferring the XFCE/KDE version (currently a release canidate)

---

### Post by oldos2er on 2012-07-17
Moved to Other OS/Distro Talk.

---

### Post by Tyluur on 2012-07-17
After getting to the install linux mint screen, I get this error:

[[IMG]http://en.zimagez.com/full/36cd6bbc3dfbd0e2329a618ec91320d413ef54021bcb031d6924c0fb25bf0a9dc68ea61caa3ace4f157d4410c464d391cf8d8ed5e1d41cf9.php[/IMG]]("http://en.zimagez.com/zimage/screenshot-07172012-123619pm.php")

---

### Post by sudodus on 2012-07-17
You have problems with EFI. I think you need to manage that if you want to keep Windows. Otherwise it would be possible to wipe the drive completely and make an old and well-known partition table with MBR etc.

Do you want to keep Windows or do you want to start with a fresh hard disk drive and install Mint only?

---

### Post by Tyluur on 2012-07-17
> **sudodus said:**
> You have problems with EFI. I think you need to manage that if you want to keep Windows. Otherwise it would be possible to wipe the drive completely and make an old and well-known partition table with MBR etc.

Do you want to keep Windows or do you want to start with a fresh hard disk drive and install Mint only?

I want to  **start with a fresh hard disk drive and install Mint only.**

---

### Post by sudodus on 2012-07-17
> **Tyluur said:**
> I want to  **start with a fresh hard disk drive and install Mint only.**
Then I suggest that you boot from your Mint install drive, run a live system (without installing anything) and run the following command to wipe your internal hdd completely:

```
sudo dd if=/dev/zero of=/dev/sd[COLOR="Red"]X[/COLOR] bs=4096
```

This should write zeros all over the drive including the partition table, but it takes hours to complete. dd does what you tell it to do, it does not ask and it does not tell anything until it has finished (unless you poke at it will a kill -USR command). So check with ```
sudo fdisk -lu
``` what drive letter to substitute for [COLOR="red"]X[/COLOR]. Probably it should be 'a', /dev/sd[COLOR="red"]a[/COLOR].

Next you can run ***gparted*** (also booted from the Mint install drive) and create an MSDOS partition table (MBR type) and make partitions if you like. Once the partition table is there, you can also let Mint's installer create partitions for you.

---

### Post by pqwoerituytrueiwoq on 2012-07-17
Looks like we got this solved (after many hours or head banging)
issue one:
had to use nomodeset to boot mint
issue two:
The 'grub-efi' package failed to install into /target/
```
sudo apt-get update;sudo apt-get install grub-efi grub-efi-amd64 grub-efi-amd64-bin
```fixed it but it then said no os found on boot

deleted this file on the Mint USB [FONT=Courier New]/efi/boot/bootx64.efi[/FONT] then it worked

the mate version would not boot like this but the xfce version did, mate can easily be installed from xfce

---

