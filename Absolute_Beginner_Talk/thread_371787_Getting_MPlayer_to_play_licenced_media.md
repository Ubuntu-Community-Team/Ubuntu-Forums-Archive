---
title: "Getting MPlayer to play licenced media"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by christiaanb on 2007-02-27
Hey guys, i'm a semi ex-win 2000 user...

Trying to switch over completely to Ubuntu. I used 6.06, and just made a fresh install with 6.10.

I've read many posts, and really appreciate everyone's help and friendliness!

Here is my question. How can I play licenced media in ubuntu. There is a website I'm subscribed to, ([www.kuduclub.com](www.kuduclub.com)) and I buy programs, but I can't get totem or MPlayer to play it.

The error I get is: Totem could not play 'mms:// (example filename) 300k.wmv'.

No URI handler implemented for "mms".

Please let me know if  need to give more info...

thanks a bunch

---

### Post by chggr on 2007-02-27
Try installing the following packets: 

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

A very good media player that can play virtual ANY file (avi, rm,  mp3, everything you can imagine) is VLC. You can install it by clicking on "Aplications" -> "Add/Remove"

---

### Post by christiaanb on 2007-02-28
Thanks, I'll check it out...

---

### Post by christiaanb on 2007-02-28
Nope, it's not working. I installed all of those, but no luck. Is there any way to install Windows Media Player through wine?

---

### Post by errantboy on 2007-04-29
Hi Christiaan,
Im also trying to figure this one out.  There is [_another thread_]("http://ubuntuforums.org/showthread.php?t=402394") about this.  It looks like Kuduclub is run by Mediazone so it should have the same DRM issues.  I'd like to know if you've had any success as it sounds like it should be possible to use WMP in wine to acquire the DRM licence.

I'm going to play about with this during the week so I'll report back if I've found anything.  The missus wants to watch Binnelanders so I'm under a considerable amount of pressure at the moment... :p

---

