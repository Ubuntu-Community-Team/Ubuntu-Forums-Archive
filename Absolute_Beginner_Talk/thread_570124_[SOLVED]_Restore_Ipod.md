---
title: "[SOLVED] Restore Ipod"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Trzone on 2007-10-07
Is there any way to restore the Ipod Nano from Linux? I know itunes is unable to run under linux.

---

### Post by n3tfury on 2007-10-07
> **Trzone said:**
> Is there any way to restore the Ipod Nano from Linux? I know itunes is unable to run under linux.

actually people have been able to use iTunes under linux using wine, but i think it's 7.x and older version of iTunes which you can get at oldversion.com.

---

### Post by Trzone on 2007-10-07
Is there any other program/way of restoring an Ipod nano besides iTunes?

---

### Post by tgalati4 on 2007-10-08
No.  Did you try the magic key press:  Hold the center and play buttons simultaneously for 10 seconds.  This is supposed to be a cold boot.

If the file system is slightly messed up on the Nano, you can use fsck to fix it.  Mount it to discover it's address (for example /dev/sda3)

Unmount it then check it.

>fsck /dev/sda3

The only time you need to do a full restore is when the file system is beyond repair.  Fsck will give you a clue based on the number of errors it has to fix.  If you fix more than a handful, then it's time to find a friend's computer to restore.

---

### Post by Trzone on 2007-10-11
why doesnt apple give a version of itunes for linux? is it due to the fact that there are so many different distributions? is there little to no market for it? is there a way for linux to decode DRM songs? or do linux users just not want to buy music from itunes? they should have a seperate way of restoring an ipod WITHOUT ITUNES.. makes perfect sense.

---

### Post by jfinkels on 2007-10-11
> **Trzone said:**
> why doesnt apple give a version of itunes for linux? is it due to the fact that there are so many different distributions? is there little to no market for it? is there a way for linux to decode DRM songs? or do linux users just not want to buy music from itunes? they should have a seperate way of restoring an ipod WITHOUT ITUNES.. makes perfect sense.

Ever get that feeling that something which seems so obvious to you is ignored by the rest of the world? Welcome to the world of open-source!

There's no Linux version of iTunes probably because it's not worth it for them to spend their resources on such a small market share (Linux has less than a percent of all OSs or something like that). Different distributions is not really a problem, there's really only a couple of different packaging formats, and if you just release the source code to your product, somebody else will package it for you (but they won't release the source to iTunes). If by 'decoding DRM songs', you mean stripping the FairPlay DRM wrapper, I'm not sure, probably. If you can do it with a Windows app, you can probably do it in Linux. We don't want to buy music from iTunes because of DRM. There was a separate way of restoring the iPod without iTunes, but they incorporated it into iTunes in a recent version.

---

### Post by Trzone on 2007-10-11
Interesting, i have tried to backup the firmware but that really did nothing, that was of course when i tried to partition it, in gparted it shows up as a 950 mb disk which is unallocated, anyways i get what you're saying.  Do all apps written for linux need to publish source code?

---

### Post by HermanAB on 2007-10-11
Yes, with gtkpod.  It works a lot better than the itunes program on Windoze.

See this: [http://www.aeronetworks.ca/ipod-howto.html](http://www.aeronetworks.ca/ipod-howto.html)

Cheers,

Herman

---

### Post by jfinkels on 2007-10-11
> **Trzone said:**
> Do all apps written for linux need to publish source code?
No. However, most developers for Linux applications choose to license their programs under some kind of free software license, the most notable being GNU General Public License, or "GPL" (you will see a lot of talk about this license in particular), which requires that the source be distributed in conjunction with the executable files. See here for more info on the four software freedoms: [http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)
> **HermanAB said:**
> Yes, with gtkpod.  It works a lot better than the itunes program on Windoze.

See this: [http://www.aeronetworks.ca/ipod-howto.html](http://www.aeronetworks.ca/ipod-howto.html)

Oh! I didn't know gtkpod restores iPods....Trzone, take a look at that. :D

---

### Post by Trzone on 2007-10-19
Hmm sorry about the long wait.. how can you restore it through gtk pod? i  figured out it'll create the ipod's folders and such.. is this it?

---

