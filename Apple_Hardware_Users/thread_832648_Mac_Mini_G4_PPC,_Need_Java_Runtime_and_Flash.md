---
title: "Mac Mini G4 PPC, Need Java Runtime and Flash"
date: 2008-06-17
forum: Apple Hardware Users
---

### Post by SouthernPott on 2008-06-17
[http://ubuntuforums.org/showthread.php?t=832221](http://ubuntuforums.org/showthread.php?t=832221)

Forgive me for not moving my thread.  I don't know how.  

Anyway, I am working on a G4 PowerPC Mac Mini and I need Java Runtime Environment and Adobe Flash or something equivalent.  I am also trying to find a way to run PokerStars.  The PC download is a .exe and the Mac download is a .dmg.  Since there is no WINE for the PPC I need to find a way to use the .dmg I guess.  I found something on Sourceforge but I either didn't understand or it didn't work.

I will need very specific instructions.

---

### Post by cyberdork33 on 2008-06-17
> **SouthernPott said:**
> [http://ubuntuforums.org/showthread.php?t=832221](http://ubuntuforums.org/showthread.php?t=832221)

Forgive me for not moving my thread.  I don't know how.Use the report function and a mod will gladly move it for you!

> **SouthernPott said:**
> Anyway, I am working on a G4 PowerPC Mac Mini and I need Java Runtime Environment and Adobe Flash or something equivalent.
I think this will answer your questions... or at least get you started.
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

> **SouthernPott said:**
> I am also trying to find a way to run PokerStars.  The PC download is a .exe and the Mac download is a .dmg.  Since there is no WINE for the PPC I need to find a way to use the .dmg I guess.  I found something on Sourceforge but I either didn't understand or it didn't work.
You might be out-of-luck there. Mac binaries are not compatible with Linux. and windows binaries need wine or a VM. Might have to stick to OSX for that one. Maybe if you can link to that sourceforge page you are talking about I could offer some better info.

---

### Post by SouthernPott on 2008-06-18
[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

I followed the directions but the return I got indicated whatever the PokerStars download is is not a true Mac image from what I gather.

Thanks for the link to the wiki.  I will read up on it in the morning.

I have been thinking I was going to have to stick to OS X on this one.  Too bad I did a single install with Ubuntu and got rid of 10.4.  Guess I will have to shop eBay for it.  I looked at the link from the group that is doing the WINE for Linux on Mac but it isn't ready for someone as limited as me.

---

### Post by cyberdork33 on 2008-06-18
> **SouthernPott said:**
> [http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

I followed the directions but the return I got indicated whatever the PokerStars download is is not a true Mac image from what I gather.ah that is just showing how to extract the contents of the image file. You will find, once the files are extracted, they will likely not be very helpful.:(

I think that you can just mount the image though if you want.

```
sudo mkdir /media/DMGFolder
sudo mount -t hfs -o loop dmg_filename.dmg /media/DMGFolder
```

Then when you are done, you can unmount it:
```
sudo umount /media/DMGFolder
sudo rmdir /media/DMGFolder
```

---

