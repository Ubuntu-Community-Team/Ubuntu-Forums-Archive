---
title: "Can't Play CERTAIN DVDs"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by golem3 on 2007-02-06
I know all about libdvdcss, codecs, automatix2, etc. etc.

I can't help but wonder **why certain DVDs (namely new ones) cannot be played on Totem**, or on any of the five major playback programs, while old ones work perfectly. Anyone help me out here? 

For example, *Solaris* plays but not *Prairie Home Companion.*

---

### Post by ComplexNumber on 2007-02-06
> **golem3 said:**
> I know all about libdvdcss, codecs, automatix2, etc. etc.

I can't help but wonder **why certain DVDs (namely new ones) cannot be played on Totem**, or on any of the five major playback programs, while old ones work perfectly. Anyone help me out here? 

For example, *Solaris* plays but not *Prairie Home Companion.*
do you use the gstreamer engine for totem? you can find out by firing up synaptic and looking for totem. if you have totem-gstreamer installed instead of totem-xine, then there is where part of the problem is. i found gstreamer to be quite restricted compared to xine when it came to totem.
i suspect that it may be something else in addition to that, but i'll wait for your answer.

---

### Post by golem3 on 2007-02-07
> **ComplexNumber said:**
> do you use the gstreamer engine for totem? you can find out by firing up synaptic and looking for totem. if you have totem-gstreamer installed instead of totem-xine, then there is where part of the problem is. i found gstreamer to be quite restricted compared to xine when it came to totem.
i suspect that it may be something else in addition to that, but i'll wait for your answer.

@ComplexNumber - THAT DID THE TRICK! Thanks a lot! 

This is my fifth Ubuntu install, and I haven't had this issue. In the past, I suppose, totem-xine was installed by default. Why would gstreamer be installed now? 

MOREOVER, what is the point of gstreamer, and why does it exist? It seems that only xine should be used!

---

### Post by Sunflower1970 on 2007-02-07
Glad I found this post! I was having that trouble the other night with a DVD. I thought it was the DVD player I was using. I have two in one computer--one very old--at least 9 yrs, and a newer one. It wouldn't play on the newer one, but the old one played the DVD just fine. Weird.

---

### Post by protenniser on 2008-01-29
@ComplexNumber:

You are a real hero, thanks for the solution.... :)

---

### Post by stchman on 2008-01-29
> **golem3 said:**
> I know all about libdvdcss, codecs, automatix2, etc. etc.

I can't help but wonder **why certain DVDs (namely new ones) cannot be played on Totem**, or on any of the five major playback programs, while old ones work perfectly. Anyone help me out here? 

For example, *Solaris* plays but not *Prairie Home Companion.*

I personally use VLC.  It does a far better job of playing DVDs than Totem.  Totem does not support menus like VLC does.  Use 

vlc %m

in the removable media section.

---

### Post by protenniser on 2008-01-29
Hi,

The funny part is that with g-streamer backend it doesn't matter which player you use for me (it didn't work with VLC either.). However after installing the xine-backend, all players work very well.
Of course still this might be my case.

Regards...

---

