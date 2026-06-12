---
title: "Unzipping ISO"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-12-24
Is there any way to ¨Unzip¨ an ISO image? My brother has a program ¨Extract now¨ on his Windows machine that can do this. I have downloaded 7zip but cannot find or run the damn thing. Please, any other apps, methods or help will be greatly appreciated! :)

---

### Post by bodhi.zazen on 2006-12-24
It can be done, but usually *.iso files are either burned to a disk or mounted.

If mounted they are then available just like any directory.

```
sudo mkdir /media/iso
sudo mount -o loop -t iso9660 filename.iso /media/iso
```

Then browse or list /media/iso

---

### Post by RudolfMDLT on 2006-12-24
Thats pretty powerful! Very cool! thanks! :-D

---

### Post by PurplePenguin on 2006-12-24
I didn't know that they could be mounted so easily, too!  This reminds me of when I searched high and low for a program that could resize all of the photos I had in a directory... the somebody told me about the mogrify command.  There's a lot of great, powerful stuff hidden away in the average linux distro. :D

---

### Post by nhandler on 2006-12-24
Right click the iso, and hit 'open with archive manager'. From there, you should be able to extract the iso to any folder you want.

---

### Post by RudolfMDLT on 2006-12-25
No suck option in KDE - What manager are you using exactly?

---

