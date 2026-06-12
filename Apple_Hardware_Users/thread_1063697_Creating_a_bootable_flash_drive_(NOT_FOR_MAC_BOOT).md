---
title: "Creating a bootable flash drive (NOT FOR MAC BOOT)"
date: 2009-02-08
forum: Apple Hardware Users
---

### Post by Jaiibee on 2009-02-08
I have an Asus EEE PC 701 without an operating system on it.
I have a Mac G5 PPC, with mac os x 10.4 on it.
I have an imation nano, 4GB flash drive.
I have the .iso for Easy Peasy which I want to install to my Asus EEE PC 701.

[SIZE=4]What I've done
[/SIZE][INDENT]
[LIST=1]
[*]Uploaded contents of EP (Easy Peasy) to my Imation Nano 4GB Flash Drive.
[*]Plugged the USB into my EEE PC and attempted to boot from it. I got a black screen with flashing cursor (underline version)
[*]Plugged my Flash Drive back into my mac and changed the folder isolinux to syslinux, and file isolinx/isolinux.cfg to isolinux/syslinux.cfg

My new structure for this is..
/autorun.inf
/casper
/dists
/install
/syslinux
---syslinux.cfg
/md5sum.txt
/pool
/pics
/preseed
/README.diskdefines
umenu.exe
wubi.exe
(wtf at the .exe, ay?)

This structure does not show all the files and is there only to show the change from isolinux to syslinux more clearly.
[*]Attempted to boot from that, but I got the black screen with a flashing cursor again.
[/LIST]
[/INDENT][SIZE=4]My Assumption..
[/SIZE][INDENT]...is that the Flash Drive has not been configured for booting. So, I've looked around but majority of things are "boot from CD and install to USB" or "disk utlity" or it's for booting Max OS X from a flash drive.
That said, I'm at a complete loss, whilst being left completely frustrated as I need to take this laptop to school in 10 hours, and it'll be another day of it over heating etc.
[/INDENT][SIZE=4]My Question
[/SIZE][INDENT]How can I use my Mac OS X 10.4 to configure a Flash Drive for booting?

[/INDENT]Just to get it out of my system... [SIZE=5][SIZE=3]I am not booting anything on my mac, nor am i booting os x.[/SIZE]

[/SIZE]Feels good to do that, sorry.[SIZE=5]
[SIZE=1]
Any and all help will be greatly appreciated :)[/SIZE]
[/SIZE]

---

### Post by mkvnmtr on 2009-02-08
I believe you will have to use Disk Utility to burn the ISO to the disk.I use my mac os so seldom I can't tell you exactly how but I would have the ISO on the desk top and the stick plugged in. Then find what it takes to burn to the stick. Maybe a google will find you something if it is not evident in disk utility how to do it.

---

### Post by Jaiibee on 2009-02-08
I tried that before, but there is a possibility that the .iso was corrupt, so I'll try again when I get home.

Does the Disk Utility make the actual flash drive bootable though? ANd not just transfer the files onto it..

---

### Post by Jaiibee on 2009-02-09
Performed the suggested method.
Did a disk utility to restore my flash drive, however it didn't work. I still get a flashing cursor.

---

### Post by cyberdork33 on 2009-02-09
for isolinux / syslinux, I believe there is more to it than just copying a file into place... You actually have to run a command to install the loader correctly. I don't know if this is possibly from within OSX.

---

### Post by snowpine on 2009-02-09
Easiest method:

1. Burn a Ubuntu 8.10 Live CD (if you don't already have one)
2. Boot with the Live CD
3a. Run the "Create a USB" utility in the System menu to create a bootable USB from the Easy Peasy iso
OR
3b. Download the Unetbootin utility (I recommend the .deb version) and use it to create a bootable USB from the Easy Peasy iso

I do not think Unetbootin is available for Mac, hence my suggestion to use the Ubuntu Live CD instead.

You could also check out pendrivelinux.com if you are looking for more suggestions.

Alternate method: Buy or borrow an external USB CD-ROM drive and install Easy Peasy from a live CD.

---

### Post by cyberdork33 on 2009-02-09
> **snowpine said:**
> Easiest method:

1. Burn a Ubuntu 8.10 Live CD (if you don't already have one)
2. Boot with the Live CD
3a. Run the "Create a USB" utility in the System menu to create a bootable USB from the Easy Peasy iso
OR
3b. Download the Unetbootin utility (I recommend the .deb version) and use it to create a bootable USB from the Easy Peasy iso

I do not think Unetbootin is available for Mac, hence my suggestion to use the Ubuntu Live CD instead.

You could also check out pendrivelinux.com if you are looking for more suggestions.
I think the issue he will run into here is that is Mac is PowerPC architecture. It is not that easy to "boot with the LiveCD". and even he does get that part done, I don't think there is the option to install to USB because the packages will be powerpc packages on the disc.

---

### Post by snowpine on 2009-02-09
> **cyberdork33 said:**
> I think the issue he will run into here is that is Mac is PowerPC architecture. It is not that easy to "boot with the LiveCD". and even he does get that part done, I don't think there is the option to install to USB because the packages will be powerpc packages on the disc.

Ubuntu is available for PowerPC: [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

And it does not matter which architecture he boots from because he will be copying the easy peasy .iso to the flash drive, not Ubuntu 8.10. :)

(edit) I stand corrected; the link I just posted is for an alternate installer, not a live cd. Sorry!!

---

### Post by card_ace on 2009-02-09
i'm not sure if this is what you want, but a few months back i was trying to find out how to install to my external hard drive.  I found this program called "bootit" that will switch something in the flash drive and enable it to be bootable.  however, i think you need a windows os to use it, and unfortunately i can't remember the link.  I think your best bet would be to do a google search or something.  hope this helps

---

### Post by ajmctaggart on 2009-02-09
Basically, You make two partitions on the flash drive from Disk Utility...

1 needs to be the exact size necessary for the .iso, a few MBs won't hurt anything but make it as close as possible...

Choose the "Convert," option from the top of Disk Utility, convert the .iso, make it cd/dvd master...it will add a .cdr extension, don't worry, that boots on i386 too no problem...

Make sure the flash drive is FAT formatted, and that the bottom of Disk Utility shows it having the Partition scheme of an MBR...

You then want to restore that .cdr file to the partition on the drive that has the same size...

Obviously it would be much easier when booting from cd, but for what you need this should work...

---

### Post by snowpine on 2009-02-09
OK, there is a live cd of 8.04 for Power PC: [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

You can run Unetbootin from 8.04.

---

### Post by Jaiibee on 2009-05-17
> **ajmctaggart said:**
> Basically, You make two partitions on the flash drive from Disk Utility...

1 needs to be the exact size necessary for the .iso, a few MBs won't hurt anything but make it as close as possible...

Choose the "Convert," option from the top of Disk Utility, convert the .iso, make it cd/dvd master...it will add a .cdr extension, don't worry, that boots on i386 too no problem...

Make sure the flash drive is FAT formatted, and that the bottom of Disk Utility shows it having the Partition scheme of an MBR...

You then want to restore that .cdr file to the partition on the drive that has the same size...

Obviously it would be much easier when booting from cd, but for what you need this should work...

Everyones going to hate me, but I'm going to revive this topic because I'm back in this same boat (i never fixed it before), and I'm going to persevere and get this **** done.

Ok, so keeping things updated, I'm trying ajmctaggarts method, then I'll try snowpines if ajmctaggarts fails (because snowpines involves going into another OS, which I really cbf doing (nor do I really have the bandwidth).

I'm working with EEEbuntu now, so yeah.. a little different but should provide answers for the googlers.

I'll keep you guys updated.

Edit: I don't have FAT formatting.. I have MBR as the partition but I can't see FAT. I have MAC OS Extended, etc., UNIX file system and MS-DOS File System.

But, because "It was developed by Bill Gates and Marc McDonald during 1976&#8211;1977" (from wikipedia), i'm going to try MS-DOS and I'll see how I go :)

Edit: For the googlers, MBR = Master Boot Record :)

Edit3: Geez, I can't make an MS-DOS partition of more than 553.4MB... :\

---

