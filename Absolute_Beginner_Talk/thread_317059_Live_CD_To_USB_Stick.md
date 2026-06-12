---
title: "Live CD To USB Stick"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by 2222 on 2006-12-11
:confused: I have read several posts about creating a bootable Linux flash drive but this has always involved using a standard Linux install.

What I'd like to have is running live-CD ISOs (i.e. their files) from a USB drive, because I anticipate much better system response times than those experienced with CDs.

I am able to create a bootable USB stick with syslinux but I have not the slightest idea how to instruct (K)Ubuntu that it should regard my flash drive as the CD replacement for booting. Just copying the files obviously did not work.

One more problem is how to create a pre-boot CD in order to continue booting live-CD contents from the USB stick (one of my computers does not boot from USB devices).

Any help is greatly appreciated.
Thanks.

---

### Post by thelinux_guy on 2006-12-11
> **2222 said:**
> :confused: I have read several posts about creating a bootable Linux flash drive but this has always involved using a standard Linux install.

What I'd like to have is running live-CD ISOs (i.e. their files) from a USB drive, because I anticipate much better system response times than those experienced with CDs.

I am able to create a bootable USB stick with syslinux but I have not the slightest idea how to instruct (K)Ubuntu that it should regard my flash drive as the CD replacement for booting. Just copying the files obviously did not work.

One more problem is how to create a pre-boot CD in order to continue booting live-CD contents from the USB stick (one of my computers does not boot from USB devices).

Any help is greatly appreciated.
Thanks.

Follow this guide:

1st make sure that your computer can bood from USB

2nd insert your Flash media into the proper drives,put you Ubuntu CD-ROM disk (ubuntu,kubuntu,edubuntu,xubuntu)into one of the drives on your computer (must be able to boot from it).restart your computer

3rd Make sure that your BIOS will boot from the drive that has the Ubuntu CD in it

4th you will see boot options from the Ubuntu start-up menu (install ubuntu,reboot,extra boot options,ect)select install ubuntu

5th your computer will begin to boot Ubuntu as soon as you select install ubuntu,this dosent directly install ubuntu but starts a desktop known as a live-CD,this is like running the whole OS from the CD

6th wait for ubuntu to come to life,when it is done booting,you should see a desktop,look for the "install" icon and double-click it

7th fill in all necessary info till you get a message that says "starting up the partitioner" at this point,you should know what the name of the flash-device you will be installing to is,and if it will be big enough (unbuntu needs 4 GB to function properly)

if you know all the info about the flash device you will be installing to is,and how to continue to the final-syeps,then your done

NOTE: besure that you know what you are doing,making a mistake (installing ubuntu to the wrong drive) can be bad. make backups and remember,dada can not be recovered after installing ubuntu.

-jason

---

### Post by 2222 on 2006-12-11
See - and that is exactly my problem: Everyone is giving advice how to install Linux on a USB stick but nobody seems to know how to run live-CD contents from it.

But thanks anyway.

Remark: I definitely don't want Linux to create a swap partition on my USB sticks and wear them down this way. Some of those items are just rated for 10k write cycles ...

---

### Post by CoolHand on 2006-12-12
I know exactly what you are asking and I like the idea as well.  Basically you want to put the CD image on the USB stick to get the faster access and boot from there but still be booting the "live CD".

I don't have a USB drive large enough handy to try but have you tried using tar to just tar up the complete contents of the CD and move it to the USB drive and then edit the syslinux setup?  Just a thought.  Good luck and please post a quick howto if you get it working.

---

### Post by thom83 on 2007-01-02
Look at that :
[http://ubuntuforums.org/showpost.php?p=1229101&postcount=158](http://ubuntuforums.org/showpost.php?p=1229101&postcount=158)
and particularly that
[http://ubuntuforums.org/showpost.php?p=1471156&postcount=174](http://ubuntuforums.org/showpost.php?p=1471156&postcount=174)
and this for patching initrd :
[https://wiki.ubuntu.com/CustomizedInitrd](https://wiki.ubuntu.com/CustomizedInitrd)
Good luck.

---

### Post by nhandler on 2007-01-02
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

That site worked for me. There's also a forum thread somewhere that talks about running Beryl (or maybe it was Breezy) to a flash drive

---

### Post by thom83 on 2007-01-03
For Breezy on flash disk, there is a link :
[http://kizl.homelinux.com/?page_id=8](http://kizl.homelinux.com/?page_id=8)
My links above are for Dapper and (maybe) for Edgy.
For the boot cd of Dapper I have 2 directories :
_casper_ with a copy of customized initrd.gz, vmlinuz, mt86plus
_isolinux_ (copy of the directory from cd) in which I modofied the file isolinux.cfg like that :

```
#    DEFAULT /casper/vmlinuz
DEFAULT custom
GFXBOOT bootlogo
#GFXBOOT-BACKGROUND 0xB6875A
APPEND   preseed/file=preseed/ltsp.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL custom
  menu label ^Start Ubuntu in persistent mode
  kernel /casper/vmlinuz
  append   preseed/file=preseed/ltsp.seed boot=casper persistent initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL live
  menu label ^Start or install Ubuntu
  kernel /casper/vmlinuz
  append   preseed/file=preseed/ltsp.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel /casper/vmlinuz
  append   preseed/file=preseed/ltsp.seed boot=casper xforcevesa initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  preseed/file=preseed/ltsp.seed boot=casper integrity-check initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

---

### Post by redPirate on 2007-05-31
This site explains step by step to prepare a USB-Live Disk for Ubuntu. It shows how to make the USB exactly as a live CD and even allows you to modify the packages which are avaliable in the Live CD.

I am sure this is the thing you need.

---

### Post by redPirate on 2007-05-31
Oops ! Sorry forgot to include the link to the site :-)

[http://www.edoceo.com/liber/ubuntu-live-usb.php](http://www.edoceo.com/liber/ubuntu-live-usb.php)

---

