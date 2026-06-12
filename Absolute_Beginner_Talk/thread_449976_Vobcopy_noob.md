---
title: "Vobcopy noob"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-05-20
I have been using vobcopy to rip dvds to my pc. They play fine, but I tried burning the .vob files directly to a disc, and lost the sound. The picture quality was also like watching a vcr that needed the heads cleaned. Is there any way to convert the .vob files to an .iso, or did I just brun the files wrong the first time?

---

### Post by mr_niceguy on 2007-05-22
You can always use something like genisoimage (check out the man page) to generate a DVD image. There may even be a gui for doing that, I don't know.

Because I like DVD's to just insert-and-play I sometimes use DeVeDe to simply create menu-less DVD iso's. As you select files for the DVD you can select the vob's you ripped using vobcopy (I use vobcopy's -l option to save each film to one big file) and then under 'advanced/misc' you can check the box that says something like 'This file is already a DVD suitable MPEG...' so it doesn't re-encode the thing.

---

### Post by OzzyFrank on 2007-07-13
Hmm.. I used **vobcopy -f -F 64 -l **and got perfect results, so maybe you missed something in the burning? This saved me many hours compared to doing it in Windows ([http://ubuntuforums.org/showthread.php?p=3016611#post3016611](http://ubuntuforums.org/showthread.php?p=3016611#post3016611)), but I admit I then took the .vob file into Windows and used IFO Edit to create the IFOs etc, and then DVD Shrink to cut out what I didn't need and fit it on a single layer disc.

---

### Post by vanadium on 2007-07-14
I guess the DVD of the first poster was encrypted. vobcopy will happily copy the VOB's as is. Apparently, an encrypted VOB can still be played, but the output is garbled. I do not know of a way to reuse VOB's directly for authoring a new DVD. Apparently OzzyFrank knows the trick by creating/editing appropriate IFO files, but I guess that required a good understanding of the internals of DVD authoring, and the software to do this in Linux might be lacking. My approach would be to demux the audio and video to DVD compliant mpg streams then reauthor a DVD from these using dvdauthor. The demuxing can be conveniently done with the graphical tool avidemux: you open the VOB and you can directly select the clip you want and save it to an mpg file.

---

### Post by OzzyFrank on 2007-07-14
My experience is that vobcopy pretty much broke the decryption, and the garbled bits where the encryption was were appended. In Ghost Rider, there is encryption at the beginning and end, and this resulted in the Marvel Comics bit being garbled, and into the first few seconds of the movie, but then it started all over again good as new! At the end, the encryption seemed to be not in the credits, but a few minutes from the end. However, this played fine, but the garbled copy of those few seconds was appended after the end of the credits. So all I had to do was cut the ends off and voila! I should have even tried the Linux version of DVDShrink, or even the Windows one in Wine, but since I've never had luck in Windows editing VOBs without IFOs, I just decided to skip playing around and just boot into Windows and create the IFO then edit the lot in DVD Shrink. I'm sure all this can be done in Ubuntu, just didn't have time to see how. I sure was impressed with vobcopy, I must say. I think I'll get a couple of Ubuntu converts just for that command alone, hehe!

---

### Post by andrew.46 on 2007-08-06
Hi,

 Read your post about vobcopy:

> **HgBoy said:**
> I have been using vobcopy to rip dvds to my pc. They play fine, but I tried burning the .vob files directly to a disc, and lost the sound. The picture quality was also like watching a vcr that needed the heads cleaned. Is there any way to convert the .vob files to an .iso, or did I just brun the files wrong the first time?

 You would normally create an iso by using the program mkisofs which is available in the repositories.

                  Andrew

---

