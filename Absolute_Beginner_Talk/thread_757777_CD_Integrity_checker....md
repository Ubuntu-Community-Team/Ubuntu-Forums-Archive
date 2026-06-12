---
title: "CD Integrity checker..."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by BigWoop on 2008-04-17
I decided to try this as I was having problems installing on an old system, so thought I may have a bad disc.

After it's finished I get this message:

"Check Finished, errors found in 122 files!"

But the DVD seems to boot as a Live CD just fine, on the same system used to run the checker.

Is it possible that it's falsely finding bad files? Is there a way for me to check the original ISO I downloaded for errors, other than re-writing it to another disc?

Also, If the disc is bad, how should I go about preventing this in the future? 
Surely it's not because I paused and resumed the download? I have done this many times with Free Download Manager and other files never have had a problem.

Thanks for any help.

EDIT:

It appears that the MD5SUM is not correct. Is this possibly caused by many pausings/resumings of the download, and perhaps that it was downloaded from two different servers? (Althoguh both servers report the same MD5SUM)?

Anyway, I'm going to go ahead and try install it anyway, I didn't download a 4.2gb ISO and waste a DVD for nothing. 
Really irritating, but I guess I should have checked the MD5SUM before burning. 
I'd reccomend it to anyone else!

---

### Post by hyper_ch on 2008-04-17
(1) Use Bittorrent to download the file - it will auto-check the integrity of the downloaded file

(2) Burn the .iso as slow as possible

---

### Post by zvacet on 2008-04-17
@ **BigWoop**

>  Is there a way for me to check the original ISO

Yes,it is.[Here.]("https://help.ubuntu.com/community/HowToMD5SUM") As **hyper_ch** said you can check iso with torrent client.Download same iso and point download to the forlder with existing iso.That way torrent will just check your iso and replace corrupted files.Run md5sum again and if it is O.K. burn iso on lower possible speed.Check disc for errors and if all goes fine install.

---

### Post by BigWoop on 2008-04-17
As I said, I have already established that my MD5SUM is incorrect.
I'll try to see if torrenting can repair my download.

EDIT:

I was sceptical as to whether your suggestions would work, but I'm trying it right now and it appears that uTorrent is filling in some missing files. So it appears to be working, I'll let you know if I have success.

---

### Post by /etc/init.d/ on 2008-04-17
> **BigWoop said:**
> 
Anyway, I'm going to go ahead and try install it anyway, I didn't download a 4.2gb ISO and waste a DVD for nothing. 
Really irritating, but I guess I should have checked the MD5SUM before burning. 

You may change your mind when the installation fails halfway through because of bad packages, or you end up with a broken system that you have to then reinstall anyway.

DVDs are cheap, your time probably isn't.

---

### Post by BigWoop on 2008-04-17
True but I'm not installing it on my main system, so if it bombs out it won't be too much trouble.

Anyway hopefully hyper_ch's and zvacet's suggestion works...

---

