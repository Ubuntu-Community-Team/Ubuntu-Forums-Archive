---
title: "[SOLVED] Formatting my Toshiba external hard drive to ext3"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Skatertjah on 2008-04-20
Heey,
I've been using Linux (Ubuntu) for quite a while now and decided to reformat my 250 gig external hard drive to the ext3 file system. I just had a few questions before I do this:
- Will the drive perform normally after formatting to ext3?
- Will the speed of the drive be affected (the drive has a speed capability of 7200 rpm)?
- Do I need any drivers afterwards?
- Will I get clicks and ticks? (I read about this on the forum ([http://ubuntuforums.org/showthread.php?t=642562](http://ubuntuforums.org/showthread.php?t=642562)) it seemed weird to me but if it is supposed to do this it will be ok)
Thanks

---

### Post by LaRoza on 2008-04-20
> **Skatertjah said:**
> Heey,
I've been using Linux (Ubuntu) for quite a while now and decided to reformat my 250 gig external hard drive to the ext3 file system. I just had a few questions before I do this:
- Will the drive perform normally after formatting to ext3?
- Will the speed of the drive be affected (the drive has a speed capability of 7200 rpm)?
- Do I need any drivers afterwards?
- Will I get clicks and ticks? (I read about this on the forum ([http://ubuntuforums.org/showthread.php?t=642562](http://ubuntuforums.org/showthread.php?t=642562)) it seemed weird to me but if it is supposed to do this it will be ok)
Thanks

* Yes, why wouldn't it?
* No, why would it?
* For Linux, no.
* No, I never had that.

---

### Post by indiecast on 2008-04-20
your drive should be fine

no drivers needed

shouldn't have any speed difference

looks like clicks and ticks is part of pre-caching or something so sounds like that's normal


BUT

keep in mind you wont be able to read your drive with a Windows PC without special software.  as this is an external hdd i would express some concern to this as you may want to take the drive to a friends house, different compy, etc.


hope this helps ur descisions,
indiecast

---

### Post by Skatertjah on 2008-04-21
Thanks a lot for replying,
I will format my hard drive to ext3, if I wanted to take it to a friends house I'll just bring a liveCD as well then it should be fine for watching movies, and file sharing wouldn't it?
If I change my mind I can just format it back to NTFS anyway...
Thanks again for replying.

---

### Post by indiecast on 2008-04-21
umm the live cd would be fine for filesharing

idk about movies unless ur friends compy has a killer cpu and tons of ram.


i dont see why you need ext3 on ur portable.  fat32 or vfat (i think)  can be read by anything

---

### Post by Skatertjah on 2008-05-25
I reformatted my hard drive and it works even better then the NTFS I used to have!
Thanks to all!

---

### Post by Nycticorax on 2008-06-26
@indiecast: yeah, but you can't have symlinks, and the permissions and ownerships have different characteristics, and it doesn't even recognise the diference between upper and lower case in file names. All that makes it really annoying to use a vfat-formatted hard drive as a back up for a linux partition. Well, that's why I'm reading this thread anyway, because I'm reformatting my vfat external hard drive to ext3.

---

