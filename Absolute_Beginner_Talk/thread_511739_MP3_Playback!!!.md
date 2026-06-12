---
title: "MP3 Playback!!!"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-07-28
Guys one small query....
On my ubuntu box Rythmbox plays mp3 files...(well i downloaded and installed the codecs...) but Amarock does not!!! why is that so and how do i fix it???:confused:

---

### Post by p_quarles on 2007-07-28
According to the wiki:
>  Amarok folks pay attention to this: if you use **libxine-extracodecs** together with **gstreamer0.10-plugins-ugly** installed, the sound of playing mp3 will become weird. Simply remove **gstreamer0.10-plugins-ugly**.
Read the full article here:
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

### Post by forestpixie on 2007-07-28
I found that I needed to install libxine-extracodecs as well as libxine1-ffmpeg

---

### Post by badguyanil on 2007-07-28
> Ubuntu 6.06 LTS (Dapper Drake)

    *

      Amarok folks pay attention to this: if you use libxine-extracodecs together with gstreamer0.10-plugins-ugly installed, the sound of playing mp3 will become weird. Simply remove gstreamer0.10-plugins-ugly.
    *

      Install the package gstreamer0.10-plugins-ugly.


are the 2 points not contradictory! i mean Remove the same package and install it again. Anyways  did this and it is working......
> To play mp3's with Amarok, install the package libxine1-ffmpeg (which will install libmad0 as well). 
Thanks for the help!

---

### Post by p_quarles on 2007-07-28
> are the 2 points not contradictory! i mean Remove the same package and install it again. Anyways did this and it is working......
Badly written, yes, but not contradictory. If you're using Amarok, you need to remove the ugly gstreamer plugins. The following line is meant for everyone else (i.e, those not using Amarok). But yes, I tripped over that when I first read it as well. 

Glad you got it working.

---

