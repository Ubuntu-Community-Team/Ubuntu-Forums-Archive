---
title: "DVD Playback"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2006-07-16
I am running Drapper Drake 6.06 64-bit edition. I have a DVD +/- Optical drive, and I have all multimedia restricted libraries installed. When I put the DVD Finding Nemo into my disk it is read and an icon appears on my desktop labled as Finding Nemo, I can read it's contents, it is stored at /media/cdrom0, but I can't chmod the file, or chown the file. I don't know how to play the .vob files but I've tried in Xine, Gxine, Totem, MPlayer, and Ogle, with no luck. The file video_ts.vob will play, but none of the others will. The errors returned are:

Totem:
> 
Totem could not play 'file:///media/cdrom0/video_ts/vts_01_1.vob'.


MPlayer:
> 
Error. Seek Failed.


Totem:
> 
Read Error From:

*Then crashes*

Xine:
> 
The source can't be read.


Any help?

-Ryan H

---

### Post by GuitarHero on 2006-07-16
[http://en.wikipedia.org/wiki/VOB](http://en.wikipedia.org/wiki/VOB)

I think you need VLC

---

### Post by Anduu on 2006-07-16
Just curious why do you need to access the vob file at all...just play the DVD.

---

### Post by Ryan H on 2006-07-16
How do I just play the DVD?

-Ryan H

---

### Post by Thenotsowyzewun on 2006-07-16
Ubuntu can't play proprietary formats in it's default installation.

Click here for a guide to [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

More specifically, here's the information you need: [DVD Playback]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9").

---

### Post by TheMono on 2006-07-16
In GXine - just click File>DVD

On my system, starts the disc straight away.

Oh, and Thenotsowyzewun, he mentions earlier that he already has the restricted stuff installed.

---

### Post by Thenotsowyzewun on 2006-07-16
> **TheMono said:**
> Oh, and Thenotsowyzewun, he mentions earlier that he already has the restricted stuff installed.

Oops, I should read posts properly before replying!

---

### Post by Ryan H on 2006-07-16
When I click File > DVD, it says on the screen "MPEG Block". And doesn't play.

-Ryan H

---

### Post by Anduu on 2006-07-16
I have found MPlayer to be the easiest to play DVDs with.

Just start MPlayer from the menu then right click the empty video screen and select DVD>Open Disk...

---

### Post by Ryan H on 2006-07-16
It gave me:
> 
Error!
Failed to open dvd://1


-Ryan H

---

### Post by Anduu on 2006-07-16
Ok try this....

Right click the mplayer window and select preferences...go to the Misc tab.At the bottom it lists DVD device and CDROM device...these entries should correspond to where your DVD and CDROM are mounted.

If they don't change them to match.If they do I dont think you have the multimedia codecs installed properly.

To see where your disks are mounted :

In the gnome menu go to System>Administration>Disks...

---

