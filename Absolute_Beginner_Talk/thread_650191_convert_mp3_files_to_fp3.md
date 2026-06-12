---
title: "convert mp3 files to fp3"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by stephanecharette on 2007-12-26
For Christmas, our 2 kids received "Fisher Price Fp3" players.  Of course the software is only for Windows.  These players cannot play .mp3 files.  Only "fp3" files.  When connected via USB to my Ubuntu 7.10 workstation, I can see the drive as /dev/sdc1.  It looks like this:

/dev/sdc1 on /media/disk-1 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

There are no folders, just a handful of files in the root directory.  Including the .fp3 music files.

If anyone discovers how to convert from mp3 to fp3 within linux without touching Windows, please reply to this thread.  :)

Stéphane Charette

---

### Post by slughappy1 on 2007-12-26
have you tried to install the program with wine?

---

### Post by IgnacioMiller on 2007-12-26
I've been doing some google searches, and I have read that there is no conversion utility for Windows, nevermind any other operating system. The only thing I can think to try (right now) is to simply rename your .mp3 files to. fp3, and drop them in the storage volume. Can't hurt to try! lol

---

### Post by Hospadar on 2007-12-26
I would bet that if anything is different other than the filename, it's relatively minor (maybe some specific id3 tagging) so I would bet whatever software came with them would work under wine.

Have you tried plopping one of the fp3 files into linux and seeing if anything will play it?  that would be a good indicator of any differences between the file formats

Wine's ubuntu installation page: 
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
once you get it installed, go to a command line run "wine setup.exe" or whatever the name of the program file is to convert things

---

### Post by vraicovi on 2008-01-07
I've pulled my hair out with this as well.  If someone is interested in playing around with an FP3 file, shoot me a PM with your email and I'll send you an FP3 file.

I've tried renaming the files to everything under the sun with no luck.  I've looked at the files in text editors and there are no tell tale signs like in other formats.

---

