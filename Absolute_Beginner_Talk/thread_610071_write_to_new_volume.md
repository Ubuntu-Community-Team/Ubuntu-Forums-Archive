---
title: "write to new volume"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by buccaneere on 2007-11-11
I got an HDD formatted NTFS, read on USB by ubuntu as 'new volume'.

How do I open it to see that all 80G is available on this empty drive? 

Right now, I cannot even write to it. What isn't done yet, to give me 'write'/'copy to' access???

Thanks

---

### Post by mkoehler on 2007-11-11
Buccaneere,

    You'll have to install the NTFS 3G driver: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Cheers!

---

### Post by buccaneere on 2007-11-11
> **mkoehler said:**
> Buccaneere,

    You'll have to install the NTFS 3G driver: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Cheers!

Thanks there koeler...

The ubuntu machine is offline / off network. This NTFS 3G driver I presume I burn to disk on another box, then load into the ubuntu box?

Could I change permission by pulling the USB HDD, and formatting it in a windows machine fat32?

---

### Post by mkoehler on 2007-11-11
Buccaneere,

     As of now, Ubuntu only has read support for FAT32/NTFS partitions by default.  The NTFS 3G and vfat drivers simply allow you to add write support to the drives.  In order to write to the drive, you will either have to install the NTFS 3G or vfat driver, or you can format your drive to the ext3 (or similar) filetype, which is native to linux (note that if you change to the ext3 format, you will not be able to read the drive on a windows machine).

Cheers!

---

### Post by buccaneere on 2007-11-11
> **mkoehler said:**
> Buccaneere,

     As of now, Ubuntu only has read support for FAT32/NTFS partitions by default.  The NTFS 3G and vfat drivers simply allow you to add write support to the drives.  In order to write to the drive, you will either have to install the NTFS 3G or vfat driver, or you can format your drive to the ext3 (or similar) filetype, which is native to linux (note that if you change to the ext3 format, you will not be able to read the drive on a windows machine).

Cheers!


Thanks again...

Where is NTFS 3G app to download? Is it available in this forums to download?

---

### Post by mkoehler on 2007-11-11
Buccaneere,

      I stand corrected, you can write to an ext3 formatted drive using this driver: [http://www.fs-driver.org/](http://www.fs-driver.org/).  As for the NTFS 3G driver, I found an off-site download location at [http://flomertens.free.fr/ntfs-config/download/feisty/ntfs-config_1.0.1-1_all.deb](http://flomertens.free.fr/ntfs-config/download/feisty/ntfs-config_1.0.1-1_all.deb) - If you download that and open it using the GDebi Package Installer, you should be able to follow the instructions shown on the aforementioned page.  Note that this is for Fiesty, and I haven't read whether it will or will not work on Gutsy, but I presume that it will.

Cheers!

---

### Post by kwacka on 2007-11-11
Use synaptic and search for NTFS (as the box is not networked ensure that only the CD is in the repository list) - there's a very good chance you'll find NTFS-3g & NTFS-config on the disk.

FDISK, CFDISK & Gparted should all be able to partition/format the drive to whatever you want.

I understood the read/write problems with NTFS were sorted last year?

---

### Post by buccaneere on 2007-11-11
> **mkoehler said:**
> Buccaneere,

      I stand corrected, you can write to an ext3 formatted drive using this driver: [http://www.fs-driver.org/](http://www.fs-driver.org/).  As for the NTFS 3G driver, I found an off-site download location at [http://flomertens.free.fr/ntfs-config/download/feisty/ntfs-config_1.0.1-1_all.deb](http://flomertens.free.fr/ntfs-config/download/feisty/ntfs-config_1.0.1-1_all.deb) - If you download that and open it using the GDebi Package Installer, you should be able to follow the instructions shown on the aforementioned page.  Note that this is for Fiesty, and I haven't read whether it will or will not work on Gutsy, but I presume that it will.

Cheers!

I got the app saved, waiting to burn to CD. I cannot write it to a new blank DVD+R (so says windows vista).

Any clue?

Can I save the NTFS-CONFIG app, **from** the vista box, directly **to** the [networked] ubuntu machine???


EDIT: kwacka - I looked under synaptic package manager, and no ntfs packages are listed...

might I find this app to extract off of one of the following:

Ubuntu Edgy Eft live 
Winternals
Fedora 7 live
Fedora 7 full disc set
New Ubuntu
Tiny XP
PC linux OS

---

### Post by buccaneere on 2007-11-11
Okay, how 'bout this, to get the ntfs-config app onto the ubuntu box...

Disconnect USB NTFS HDD from Ubuntu.
Connect USB NTFS HDD to Vistabox.
Save NTFS-config to USB NTFS HDD.
Disconnect USB NTFS HDD, with app, from Vistabox.
Re-connect USB NTFS HDD, with app, to ubuntubox.
Load app onto ubuntubox.

Will ***that*** work???

---

### Post by mkoehler on 2007-11-11
There isn't any reason why Vista should be giving you this error, but if you zip up the file, you might have better luck.  On the other hand, you could download a freeware SFTP program for vista that would allow you to log onto your networked ubuntu computer.

EDIT: Yes, what you just suggested *should* work.

Cheers!

---

### Post by buccaneere on 2007-11-11
> **mkoehler said:**
> There isn't any reason why Vista should be giving you this error, but if you zip up the file, you might have better luck.  On the other hand, you could download a freeware SFTP program for vista that would allow you to log onto your networked ubuntu computer.

Cheers!


Well, it ain't exactly networked yet...

So I've now saved the app to the NTFS volume itself. Will this app load when re-connected to the ubuntu box?

---

### Post by buccaneere on 2007-11-11
> **buccaneere said:**
> Well, it ain't exactly networked yet...

So I've now saved the app to the NTFS volume itself. Will this app load when re-connected to the ubuntu box?

I've done this. 

I have several options now, as it appears on the ubuntu box:

open with gdebi package installer
....................archive manager
....................other application
copy [to] ...
extract to ...
send to...
properties

---

### Post by buccaneere on 2007-11-11
> **mkoehler said:**
> Buccaneere,

      I stand corrected, you can write to an ext3 formatted drive using this driver: [http://www.fs-driver.org/](http://www.fs-driver.org/).  As for the NTFS 3G driver, I found an off-site download location at [http://flomertens.free.fr/ntfs-config/download/feisty/ntfs-config_1.0.1-1_all.deb](http://flomertens.free.fr/ntfs-config/download/feisty/ntfs-config_1.0.1-1_all.deb) - If you download that and open it using the GDebi Package Installer, you should be able to follow the instructions shown on the aforementioned page.  Note that this is for Fiesty, and I haven't read whether it will or will not work on Gutsy, but I presume that it will.

Cheers!

I missed this before; got it now. 

AND, I got error: dependency not satisfied; python2.5

EDIT: I found python.org [COLOR="Blue"]http://www.python.org/download/[/COLOR] , with several versions of 2.x; which one do I need? I see no definitive version for linux/ubuntu/edgyeft.............

---

### Post by buccaneere on 2007-11-11
> **buccaneere said:**
> I missed this before; got it now. 

AND, I got error: dependency not satisfied; python2.5

EDIT: I found python.org [COLOR="Blue"]http://www.python.org/download/[/COLOR] , with several versions of 2.x; which one do I need? I see no definitive version for linux/ubuntu/edgyeft.............


Is this error message telling me that package python2.5 is not installed, or that it IS installed, and faulty?

Should package python2.5 be listed under synaptic package manager package list???

Help?

---

### Post by buccaneere on 2007-11-11
I've d'loaded python2.5 onto the same HDD drive, to load onto the ununtu box.

I'm guessin' it should be opened with GDebi package installer???

Here goes; watch for the mushroom cloud...


EDIT: Package python2.5/extension .msi is not the correct version. Thanks............

---

### Post by buccaneere on 2007-11-11
> **buccaneere said:**
> I've d'loaded python2.5 onto the same HDD drive, to load onto the ununtu box.

I'm guessin' it should be opened with GDebi package installer???

Here goes; watch for the mushroom cloud...


EDIT: Package python2.5/extension .msi is not the correct version. Thanks............

I got 2.5.1.tar.tar , to install, from external volume.

Options are;

Open with archive manager,
.........other application,
copy,
extract to,
send to,
properties.

Help???

---

