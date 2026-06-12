---
title: "DVD playback won't work"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-10-01
I'm trying to play Kill Bill V2 on my DVD drive, but when I tell Totem Movie Player to play it, it just crashes. Can this be fixed?

---

### Post by 3rdalbum on 2006-10-01
Do you have libdvdread and libdvdcss installed on your computer? (these are required for commercial DVD playback)

If so, then try installing GXine, MPlayer or VLC from the repositories. The backends used in these programs are much more mature than GStreamer (Totem's backend).

---

### Post by reldruH on 2006-10-01
Try easyubuntu (website [here]("http://easyubuntu.freecontrib.org/")). It's the best way I've found to install it. I've found that if you don't try and do everything at once it works much better. Just check the DVD playback box and install that. Then go back and do other stuff. It should work perfectly.

---

### Post by NewRubberSoul on 2006-10-01
Yeah, I noticed the same thing with Easy Ubuntu.  I had better results when installing 2-3 things at a time, rather than all at once.

---

### Post by keheikev on 2006-10-01
> **3rdalbum said:**
> Do you have libdvdread and libdvdcss installed on your computer? (these are required for commercial DVD playback)
Ive got both of these installed plue mplayer but it doesnt seem to find the dvd when I right click and select play dvd. It says failed play dvd/0 in a little popup I believe. If I select one of the files using the open folder option it will say failed seek. I have w32codecs installed. BTW how to make mplayer the default for dvd playback
Kiheikev

---

### Post by Incompetnce on 2007-10-02
i have a similar problem vlc doesnt playback my new DVD of 300. I couldn't find libdvdcss in synaptic...

---

### Post by philinux on 2007-10-02
libdvdcss2 is from the medibuntu repo - if you read the sticky on multimedia it tells you how to enable it.

I also had to install region-set to get mine to work even though I never actually ran region-set, weird.

---

