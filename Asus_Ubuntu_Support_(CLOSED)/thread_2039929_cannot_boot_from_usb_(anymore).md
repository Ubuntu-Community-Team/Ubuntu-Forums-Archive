---
title: "cannot boot from usb (anymore)"
date: 2012-08-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jessel on 2012-08-09
Hi,

I've been struggling with my wife's asus x101. it worked well for a little while with the meego os, then i upgraded to ubuntu 11.04. that was quite a while back. it worked great for a few months...

problem is that the machine will not boot off of usb media, sd media. that it will not auto-mount sd or usb media.

a few weeks ago i tried to upgrade to 12.04 using the installer, the installer went to work but then failed complaining that there was not space. the x101 only has an 8gb drive so i wasn't surprised even though nothing really gets downloaded or saved onto this netbook.

ok, i figured, fine i'll just download the installation on another computer and create a bootable usb disk. i did this, just like when i installed 11.04. and it did not work. 

the message that i get is simply "missing operating system"

after failing to boot i noticed that the machine would not mount the disk once it was running. there are two usb ports, and neither can see any usb device that you insert. note that i did check the usb disk by mounting on another computer, it is possible to mount the usb drive and look at the files on it. when i tried to manually mount i found that i am able to look at whats on the disk.

next i tried a bootable 16gb miscro sd flash disk. the results were the same.

next i checked the bios settings, and boot from usb is enabled.

still not able to boot from sd, or usb from either port.

next i opened the disk utility according to which the sd card reader and the usb drives are working fine. which makes sense since i can mount the drive manually. i did notice that the main solid state drive which is 8 gb is partitioned into three drives: 

sda1 - 4.8gb, primary partition
sda2 - extended-  sda5 2.1 gb swap partition

my disk utilty says i have 5.8 gb available and that 4.7 gb are used up.

any help would be appreciated.

thanks

---

### Post by 2F4U on 2012-08-10
Ok, you mounted the usb on another machine and looked at the files. But did you actually boot from the usb stick on another machine? The thing is that you may be perfectly able to look at the files, but if the bootloader is not installed correctly, it won't boot from the stick.

---

### Post by jessel on 2012-08-10
that might be it. what i thought was a usb boot disk did not boot another machine either. i looked closer at the usb disk creation instructions and it says 2gb disk minimum, well mine is 1gb. i'm going to get a 2gb disk and try it again this evening. 11.04 installed fine off of this disk, and the download is about 700mb so i never questioned it...

---

### Post by jessel on 2012-08-10
ok that was it, just needed a larger usb disk. 

12.04 works on the x101.

i'm not sure what happened as far as the problems mounting the usb and sd drives but both drives are fine, since the reinstall.

---

