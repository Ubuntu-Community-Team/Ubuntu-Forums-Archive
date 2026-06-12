---
title: "Share External HD"
date: 2007-07-08
forum: Apple Intel Users
---

### Post by dareofficer on 2007-07-08
Hello, I have a intel iMac core 2 duo.  I have it doing a dual boot ubuntu/OSX.  I have a external HD, for files that works on the mac.  I can see it in Ubuntu, how can I setup the permissions to let me read/write on the ubuntu end?

Thanks

---

### Post by cyberdork33 on 2007-07-08
what is the filesystem?

---

### Post by dareofficer on 2007-07-08
imac core2duo

OSX / Ubuntu 7.4 Fiesty

Works on OSX, and shows up on Fiesty.  Can't write on Fiesty.

---

### Post by cyberdork33 on 2007-07-08
no i mean what is the format of the drive.

If you are having trouble writing to it then I am guessing it is HFS+. You will need to disable journaling on the drive in OSX, and then set the permissions so that everybody can read & write

---

### Post by dareofficer on 2007-07-08
Okay, I see what you mean.  It was setup OSX journal.  Do I have to reformat that drive?  Or is there a way around that?

---

### Post by cyberdork33 on 2007-07-08
no, just need to disable journaling. In OSX:
From this post
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)
> 
Run this command:
```
sudo diskutil enableJournal Macintosh\ HD/ 
```of course replacing Macintosh HD with your Volume name. Bear in mind that the above is not a typo, it is supposed to read "enableJournal" even though we are trying to disable Journaling, this is due to a bug (in at least my Tiger install) that labelled the Volume as Journaled when it wasn't. After you have run the above run:

```
sudo diskutil disableJournal Macintosh\ HD/ 
```verify that it says Journaling has been disabled.

---

### Post by dareofficer on 2007-07-09
Got it and thanks.  One more question, the material already on the hd has a lock on it.  Is there a way to open that up?  If not no big deal.

Thanks again!

---

### Post by cyberdork33 on 2007-07-09
yep that is the permissions part. You will have to modify the permissions on the folders you want to share (or the entire drive if that is what you're after). If you access the drive with root permissions (sudo) then you can access all the folders and mod the permissions, or you can do it in OSX.

---

### Post by ronocdh on 2007-07-10
> **cyberdork33 said:**
> yep that is the permissions part. You will have to modify the permissions on the folders you want to share (or the entire drive if that is what you're after). If you access the drive with root permissions (sudo) then you can access all the folders and mod the permissions, or you can do it in OSX.
Changing the permissions via sudo in root will indeed let you work with the files, but I believe if you flip to OS X and work with them there, the permissions will flip back to being restrictive against Ubuntu. So definitely make sure that in OS X you allow "others" r/w capability.

---

### Post by cyberdork33 on 2007-07-10
> **ronocdh said:**
> Changing the permissions via sudo in root will indeed let you work with the files, but I believe if you flip to OS X and work with them there, the permissions will flip back to being restrictive against Ubuntu. So definitely make sure that in OS X you allow "others" r/w capability.

It doesn't matter what system you change the permissions in as they are stored in the file.

you can sudo chmod 777 a file in ubuntu, and it will keep it's permissions that way in OSX. (OR at least it should... OSX does do weird stuff sometimes) If I am completely wrong please let me know.

---

### Post by ronocdh on 2007-07-10
> **cyberdork33 said:**
> It doesn't matter what system you change the permissions in as they are stored in the file.

you can sudo chmod 777 a file in ubuntu, and it will keep it's permissions that way in OSX. (OR at least it should... OSX does do weird stuff sometimes) If I am completely wrong please let me know.
I will have to test this, but I believe that if the user does not change permissions on the HFS+ (non-journaled) partition in OS X to allow "other users" r/w privileges, and instead modifies them as root in Ubuntu (with **sudo nautilus** or something), then there will be problems later on, when the user returns to OS X and resaves a file in that directory; it will then be locked for the Ubuntu non-root user.

Modifying the permissions in OS X, however, causes the setting to stick, and Ubuntu remains happy, even if files are modified in OS X.

I hope I've explained by belief clearly; again, I will test this tonight and report back.

---

### Post by cyberdork33 on 2007-07-10
Actually, with that explanation it makes a lot more sense. OSX saves a lot of info in hidden files and probably would "repair" the changed permission. Best to do it in OSX then.

---

