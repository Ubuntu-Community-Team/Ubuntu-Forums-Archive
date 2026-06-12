---
title: "Mounting a bad ISO"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Bohlio on 2007-08-06
I need help mounting a bad ISO. When I try and mount it in Ubuntu with "mount -t iso9660 -o loop blah blah blah" I get that error message that tells you pretty much anything you just typed in could have been wrong :-( If I try to burn it with K3B, it tells me it is not a valid image file. If i try to burn it using nautilus, it tells me it is not a valid disk image. But the thing that really gets me, is that it works just fine under windows with Daemon tools... I've tried burning the ISO with the ISO recorder powertoy or whatever in windows, and it gave me a disk that physically looks like it has been written too, but both OS's recognize it as a blank disk.

Ok, so to recap... It is not valid in Ubuntu, but I can mount it using Daemon tools in windows... What do I do?
Is there any way that I could mount it using daemon tools, then use some program to make an ISO of the mounted ISO, and hope that it all works out well once I try to mount it in Ubuntu :confused: ?

Thanks in advance :D
Bohlio

---

### Post by tgm4883 on 2007-08-06
Yea you can mount it and rerip it.  Just redo how you ripped it in the first place only make sure you make it an iso.

Sounds like you didn't make it an iso the first time and instead it got renamed to iso.  And daemon tools is smart enough to figure this out and mount it anyway.

---

### Post by Bohlio on 2007-08-06
Alright, thank you, I'll try it out when i get a chance :D

Well... I just opened it using Magic ISO in WINE, and it reads it correctly.
Under Properties>Filesystem,  ISO9660 is checked, along with Joliet... So why wont any ubuntu method work??

---

### Post by tgm4883 on 2007-08-06
Not sure, perhaps try acetone?

I haven't tried it (just found it) but plan on trying it later today

[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

---

### Post by Bohlio on 2007-08-06
Well, I just got it! (I think)

What I did was, open it in MagicISO using WINE, I then extracted the data to my desktop. Then I saved the extracted data into a new ISO file. I can now mount it in Ubuntu :D Now i just hope it works correctly, as this is a game install CD...

Edit: Well... that didnt work, It wouldn't let me install with it... So I took another route. I booted up windows, loaded the bad image with Daemon Tools, then made an image from the mounted image with MagicISO. This mounted in ubuntu. But when i went to install the game, It did the same thing as before, which was tell me that it needed the 2nd disk which was already in. The problem was that winecfg was reading the first disk and even after I unmounted it, It was still considered to be mounted in Wine, so i had to manually point to the second directory in wine, and now all is good :D

---

### Post by Jimcanoa on 2007-08-06
Maybe the filesystem is damaged? try fsck with the .iso . If it turns out it's damaged you can fsck --rebuild-tree.

Don't forget, if you try this, to do a backup copy before running fsck --rebuild-tree

Nevertheless if it works fine with MagicISO under wine, no need to bother ;) Just wondering why you can't do it normally...

---

