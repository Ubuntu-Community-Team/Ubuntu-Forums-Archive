---
title: "cdrom doesnot support"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by xdirectory on 2006-12-01
i would first let you know what all do i have:-
cpu-dell gx150,p3,996mhz,256 ram,20gb hdd
floppy drive-working

[B]internalcdrom[cdrom-samsung cd master 24e]("http://castle.pricewatch.com/s/search.asp?s=cd+master+24e")
external usb cdrom asus quietrack[/B]

the problem is as soon as i try to install linux it gets stuck 
at starting point saying check the cdrom integrity 
my questions 
[SIZE="4"][LIST]
[*]isit possible to install linux by using smartbootmanager to boot from floppy then using external usb cdrom instead of internal cdrom[/LIST]
[LIST]
[*]is it possible for me to use my current internal cdrom for installation it works fine in windows xp (ubuntucd and cdrom  is working good in winxp)[/LIST]
[LIST]
[*]is it possible that i save the cd on hdd an access it to install linux as we can do with windows using startup disks commandprompt[/SIZE][/LIST]

---

### Post by louieb on 2006-12-01
As far a I know the developer quite working  on SBM before support for external USB devices was added.
>  the problem is as soon as i try to install Linux it gets stuck
at starting point saying check the cdrom integrity Never seen that message. I wonder what printed it? You can try and boot to a SBM floppy and see if that gets around the message. At what speed did you burn it? 

> is it possible that i save the CD on hdd an access it to install Linux as we can do with windows using start-up disks command promptYes, but its a pain in the ***. The only documentation on this I have seen is in the Gentoo install handbook. Be warned  the handbook is over 100 printed pages long.

---

### Post by xdirectory on 2006-12-01
hi thr ,
here i will give the error more ellobrately
livecd 6.06
boot cd 6.06
both were iso downloaded using torrent burned using nero at 12x  the media and cdrom works perfectly on xp 

1*livecd --step1:main display comes with ubuntu logo on bootup asking 
start or install
check cdrom 
check memory

when selected start or install

step2:-
shows on screen
essential drivers     ok
mounting root file system ok
then a list of checking ok---------------------------
until checking i.386.deb       ./casper/filesystem.squashfs
here system hangs for a whils says mismatch and continues reboots again to the start (tried removing the cd but boots windows )

2*bootupcd
step1:-booted using instlux  asks keyboard,language
then detecting hardware to find cdrom drives
3 min halt
then it says:-load installer components from cd 
there was a problem reading data from cdrom .please make sure it is in drive .if retrying doesnt work check integrity of cdrom 
failed to copy file from cdrom

then:-when check for cdrom integrity is done says 
the ./pool/main/b/binutils/binutils-2.16.1cvs20060117-1ubuntu2.1-powerpc.deb failed the md5 checksum verification your cdrom or the file have been corroupted at exactly 37% in the process both for livecd and bootup cd.

i am going to take a laptop soon but wanted to use linux until then anythng doesnt work then i will load redhat which i had loaded using first disk on the hard drive ,starting up with startup disk running vmlinuz the the rest 2 cds easily gets detected from cdrom(external) then i was not having a cdrom(internal).

i felt ubuntu was good for a starter rather than using redhat

---

### Post by xdirectory on 2006-12-01
thanks louie i thnk its mostly the hardware integration problem but lets see if anyone can help

---

### Post by louieb on 2006-12-01
The failed md5sum message indicates a bad cd burn.  
Being able to browse the cd in Windows means the part of the cd that holds the directory structure is ok. But there can be an install program with some bits twisted around, preventing the installation from working.
Try burning at 2x or 4x. 
My first Linux was Fedora. If you wind up useing Red Hat  that ok it not that much diffrent from Ubuntu.

---

