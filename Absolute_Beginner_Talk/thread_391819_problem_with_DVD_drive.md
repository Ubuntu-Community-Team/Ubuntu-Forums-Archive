---
title: "problem with DVD drive"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by retrodans on 2007-03-23
My DVD drive has been working fine with all data discs, and is burning fine!  I have now recently installed wine, and thought I would try to install Civilisations II onto it just to show a friend how easy it is!  Then it backfired, I cannot get into the DVDROM, the error being produced is:

> Couldn't display "CDDA:///dev/hdd", there was an error launching the application

If anyway has any suggestions on how to sort this out it would be much appreciated!

Cheers
Dan

---

### Post by dhtseany on 2007-03-23
Does this problem occur any time you try to access the drive or just when WINE tried to access it?

---

### Post by retrodans on 2007-03-23
It's everytime I access the drive with the civilizations II disc in, so when I just double click on the icon it comes up with the error!  The disc reads fine in windows.  My driver installation discs for windows worked fine, so am curious as to why this has occurred this time!

---

### Post by dhtseany on 2007-03-23
This may sound like a dumb question, but I swear I've seen it:
Is the disc all scratched up?

If not, make sure your DVD-ROM's drive letter is listed under WINE's config:

```
$ winecfg
```

---

### Post by retrodans on 2007-03-24
Okay, done some testing, the disc has superficial marks, but runs fine in my pc box.  On the linux box when I put the disc in i get the message:

> The cd in the drive contains both music and files, would you like to listen to music or browse files

If I clicke browse files here it opens the cd fine, but the second I try to open the disc from the desktop or nautilus I get the error message coming up.

Also, I am not quite sure how to check a drives letter in ubuntu, could you give me a suggestion please!

Thankyou
Dan

---

### Post by dhtseany on 2007-03-25
Ok go to the terminal and type:
```
$ winecfg 
```

Then a dialog box that looks kinda like Win2K will pop up.

Click the tab that says "Drives" and then clic the autodetect button under the drives listed and your CDROM should then appear. Click OK, then try and run your game.

Let me know what happens.

Sean

---

### Post by retrodans on 2007-03-26
Cheers, I gave that a go and it seemed to open the cd fine, I will assume it didn't work from my desktop because it was a windows disk and formatted in a strange way!

When I run the installer though it starts fine, but then closes itself, is this because it needs windows installation file system?  Just curious to check whether Civilisations II is compatible at all or whether it stopping installation is it's way of telling me NO!

Cheers for all your help
Dan

---

### Post by dhtseany on 2007-03-26
Do you know if your game requires DirectX9.0 or above? If this is the case I believe I read somewhere else on here that WINE does not yet include support for DX9+Up. So with in mind that may be why its not working for you. Hopefully in the next WINE release they include DX :)

Glad I could help

Sean

PS- The CD should read fine in your drive, CDs have their own universal file system (CDFS) just like a HDD has its own (NTFS, EXT3, FAT32, etc..)

---

