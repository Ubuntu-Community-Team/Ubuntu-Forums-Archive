---
title: "exaile problems &amp; questions -any help?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2008-03-27
i recently found out about exaile, and i love it!

few things though:

1. it keeps crashing! why!! that's so annoying!
2. is there any way of getting it to show me duplicates? or even better, remove 'em?

thanks for all your help...

---

### Post by linuxwizard on 2008-03-27
Question 1. > Check and make sure you have all gstreamer codecs installed.

---

### Post by benji.ijneb on 2008-03-28
> **linuxwizard said:**
> Question 1. > Check and make sure you have all gstreamer codecs installed.

i can't install all of them - there's loads!

---

### Post by kleo skywalker on 2008-03-28
Yeah, Exaile kept crashing for me too (if I remember right, it didn't use to on Feisty). So I tried out Listen and liked it, but it kept crashing as well.
Now I just use Rhythmbox. At least I can listen to music without interruptions this way!
> 
i can't install all of them - there's loads!
If you can get mp3 files to play, I suppose that means you have the right codecs installed already.

---

### Post by linuxwizard on 2008-03-28
benji.ijneb

This is what I had to make sure I had installed to stop Exaile from crashing and lockups. Search for these through Synaptic. Extra packages will also be installed. 
After I got all of these installed Exaile works great.

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

---

### Post by Oldsoldier2003 on 2008-03-28
> **linuxwizard said:**
> benji.ijneb

This is what I had to make sure I had installed to stop Exaile from crashing and lockups. Search for these through Synaptic. Extra packages will also be installed. 
After I got all of these installed Exaile works great.

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

lets make this easy :)

```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg
```

---

