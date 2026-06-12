---
title: "iPhone 4 (ios 6.1.2)"
date: 2013-03-12
forum: Apple Hardware Users
---

### Post by pfeiffep on 2013-03-12
I'm looking for a solution to replace iCloud on Win 7. I'm slowly adopting / learning Ubuntu's Linux in order to totally replace M$. Most of the apps found in Open Source
seem to be relatively straight forward to install and learn - Libre Office and TBird are great. Chromium browser vs Chrome - easy, Mint financial web app superb, Tax Act
 web version imports last year's Win desktop filing. Over all I'm pretty impressed with Ubuntu:popcorn:. Replacing Photoshop with GIMP will entail a pretty steep learning curve - albeit do-able. 

I'm pretty stumped inmy effort to find a straight forward, solution to iCloud - iTunes - iPhone. Most searches seemingly suggest jailbreaking:confused: the phone. Others don't seem to support 12.10. Is
this one of the tasks that, for the time being, I stick with the Win solutions?

Thanks in Advance 
Pete

---

### Post by pfeiffep on 2013-03-14
bump

---

### Post by r-senior on 2013-03-14
It depends what you mean by replace iCloud? On iOS, iCloud deals with sync'd settings and documents between devices, and device backups. The sync is all sandboxed, so one application can't generally access the iCloud documents for another. It's quite a restricted cloud implementation.

Settings and backups are pretty much iOS only. Cloud solutions like Dropbox provide a cross-platform solution for documents. The iOS Dropbox application works well and Dropbox has good support on GNU/Linux, Mac OS and Windows. Some files don't make much sense on iOS of course -- it depends whether you have an app to open them. Dropbox provide a public API for iOS apps, so some apps do have Dropbox support built in.

Ubuntu One has an iOS client but, personally, I've never really been happy with the reliability and speed of Ubuntu One file sync. I keep trying at every new Ubuntu version and it always ends up letting me down. I know others have better experiences.

iTunes doesn't run on GNU/Linux so you might be better using Mac OS or Windows to sync lots of music and video to your device. For photos, an iOS device opens up on Ubuntu like any digital camera so you can copy photos from the camera roll quite easily. Both Dropbox and (I think) Ubuntu One let you auto-sync photos to their respective clouds.

If it's email you are looking for, any IMAP-based email, e.g. GMail, works well across iOS devices and other platforms.

---

### Post by pfeiffep on 2013-03-14
Thanks for the input r-senior, your answer is thorough:) 
 
Gmail is pretty awesome - all mail and calendar are synched automatically from iPhone to ThunderBird. 
As far as music goes I only need to transfer mp3's from PC to iPhone while tethered
I'm primarily interested in the **wireless function** of synching photos from iPhone to PC directly without physically docking.
So I surmise from your answer that a dual boot Win7 ans Ubuntu 12.10 is in my future for a while.

---

### Post by r-senior on 2013-03-15
For wireless sync of photos, I think Dropbox or Ubuntu One could do the job. Both have an option to automatically sync photos from your camera roll to the cloud and therefore on to your Ubuntu machines. The iOS Dropbox app has versions for iPhone and iPad but Ubuntu One is iPhone only -- it still runs on iPad, but not full screen.

If you use that approach you might want to turn Photo Stream off on iOS so that iCloud doesn't do the same job.

For tethered sync of MP3 though, the only way I know that works is iTunes.

---

