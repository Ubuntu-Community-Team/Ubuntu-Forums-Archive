---
title: "two questions"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-10-01
1. how do i open a .rar file with 7zip ( i installed it and its not under any category in appllications, and when i chose open with from right clicking my rar file it didnt have 7zip as a choice)

2.how do i get ubuntu to detect my motorola krzr (or is it krazr?) cell phone so i can put files on it?

---

### Post by meborc on 2007-10-01
i don't know abot the 2. ... but to unrar a rar file, there is a **unrar** package available from synaptic

---

### Post by mikeyrb on 2007-10-01
As meborc said, you can open tar files with file-roller if the unrar package is installed.  Otherwise, to use 7zip, I'll just paste the contents of the description of the package p7zip-full:

> 7z and 7za file archivers with high compression ratio
p7zip is the Unix port of 7-Zip, a file archiver that archives with
very high compression ratios.

p7zip-full provides:
 - /usr/bin/7za
    a standalone version of the 7-zip tool that handles 7z archives
    (implementation of the LZMA compression algorithm) and some other
    formats.
 - /usr/bin/7z
    not only does it handle 7z but also ZIP, Zip64, CAB, RAR, ARJ,
    GZIP, BZIP2, TAR, CPIO, RPM, ISO and DEB archives. 7z compression
    is 30-50% better than ZIP compression.

p7zip provides 7zr, a light version of 7za.

 Homepage: [http://p7zip.sourceforge.net/](http://p7zip.sourceforge.net/)

Therefore it appears to be a console app, no gui.  However, there is a package named xarchive that creates a GUI frontend for p7zip.


As for number 2, there are two options.  If you add a microSD card to your phone (2GB max), your computer will recognize it the same way it does a usb flash drive.  If you don't have that, you can also access the main memory of the phone using [Moto4lin]("http://moto4lin.sourceforge.net/wiki/Main_Page") ([Directions for KRZR]("http://moto4lin.sourceforge.net/wiki/KRZR_K1")).  In either case, you may have to modify the USB settings on your phone under Settings->Connection->USB Connection.  Memory Card for memory card access, data connection for moto4lin, I believe.

Another option is to pick up a bluetooth adapter for your computer, in which case you can send files back and forth wirelessly.  You can also set it up to access the file structure wirelessly, but that's more work, and I forget how I once did that.

---

### Post by antisocialist on 2007-10-01
on krzr there are three settings options under tools and settings. none of them had a "usb settings" option

---

### Post by mikeyrb on 2007-10-01
Which carrier did you get your phone from?  Mine is a KRZR K1 from Cingular/AT&T.  It could be that you have the K1M, which is a CDMA phone, or they could have removed that option, I don't know.

The Settings menu should be in the main menu (I use the standard list menu -- not large icons).  I didn't say anything about tools and settings, so I don't know how you got there?

---

### Post by antisocialist on 2007-10-08
mines through verizon

---

### Post by mikeyrb on 2007-10-08
Yeah, Verizon is one of the more restrictive carriers in that they tend to remove useful features.  You'll have to check with them to see what options are available.

From [CNET's review of KRZR K1m]("http://reviews.cnet.com/cell-phones/motorola-krzr-k1m-verizon/4505-6454_7-31987124.html#more"):
> Bluetooth is onboard as well, but its options are limited. Though you still can't use it to transfer music files and ring tones, in a welcome move toward customer-friendliness Verizon is now offering photo transfers via that feature.

Sounds like that means you're stuck, unless you want pictures.  You could plug in the phone to the USB and see what it gets detected as.  If you're lucky, you'll get access to the memory card (you'd then have to buy one, as it doesn't come with one).  Otherwise, perhaps Moto4lin will work, I'm not sure.

---

### Post by strabes on 2007-10-08
I've had minimal success using moto4lin to connect to my RAZR v3. Then again, I can't even get it to connect in windows.

---

