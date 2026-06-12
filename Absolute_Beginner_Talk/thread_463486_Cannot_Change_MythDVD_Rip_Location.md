---
title: "Cannot Change MythDVD Rip Location"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Bubtottle on 2007-06-03
Hello
I have recently installed mythtv and am now trying to rip DVDs to watch whenever I please.
I select which titles I want and press 0. A progress bar appears and disappears so I assume it has ripped the DVD. However, when I look in MythVideo, the titles do not appear. I have no idea where the titles are saved. Looking around on the internet, all guides that could help my problem say that you need to change the location that the ripped DVDs are saved to. I have checked all the settings and cannot find anyway to do that.
I do wish to rip the files to a particular folder but if that is not possible, I would at least like to know where they are being ripped to.
Any help would be appreciated greatly.

---

### Post by daimaru on 2007-06-04
i use dvd::rip . just in case you dont find a solution for your mythtv ripping.

---

### Post by wjston on 2007-06-04
> **Bubtottle said:**
> Hello
I have recently installed mythtv and am now trying to rip DVDs to watch whenever I please.
I select which titles I want and press 0. A progress bar appears and disappears so I assume it has ripped the DVD.

Are you sure they are being ripped? How long does the progress bar stay visible?

>   I have no idea where the titles are saved. Looking around on the internet, all guides that could help my problem say that you need to change the location that the ripped DVDs are saved to. I have checked all the settings and cannot find anyway to do that.
I do wish to rip the files to a particular folder but if that is not possible, I would at least like to know where they are being ripped to.
Any help would be appreciated greatly.

You can change the location where your dvd files are ripped by going into Mythfrontend and choosing "Utilities/Setup>Setup>Media Settings>Video Settings." The first heading allows you to select/change where MythTV stores the ripped videos. This directory should have been created when you installed MythTV; however, this is not always the case. If it is not there, make sure that MythTV has read/write privileges when you create or change the directory location.

> However, when I look in MythVideo, the titles do not appear. 

After your dvd has been processed, you have to add it to your video selection. You do this by going to "Utilities/Setup>Video Manger>choose the file you just ripped(using the up/down arrows on the remote or keyboard>press the "i" key on your keyboard>MythTV will now go to the Internet Movie Database and retrieve on your movie  as well as matching Album cover. You may have to choose a title if there are more than one movie by that name. Press the "OK" button on your remote (or enter on the keyboard), and do the same again for selecting the movie poster. You should now be able to go to >Media Library>Watch Videos, and the DVD that you ripped should now be in there with whatever cover art that you selected.

Hope this helps

---

### Post by Bubtottle on 2007-06-08
Hi

Under "Utilities/Setup>Setup>Media Settings>Video Settings."  I cannot find any reference to ripping DVDs. I have, however, changed all folders to folders I am sure exist. When I attempt to rip, the progress bar shows for longer than previously, then disappears and the DVD has not been ripped.

---

### Post by jp2006 on 2007-08-01
Hi 

Just a quick note, I am having the same problem, if you change the setting to PERFECT it will rip and leave a file in the Video directory with a vob file extension, if you change this to avi it plays ok, only problem the file are huge.

Also I had to change the permissions on the video folder to allow read write access, to the right users and groups etc, then it appeared to wortk, but only on perfect setting.

All the other options I have tried don't work. 

Does anyone have any idea how to fix this

JP

---

