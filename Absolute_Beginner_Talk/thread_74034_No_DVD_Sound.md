---
title: "No DVD Sound"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by Velouria on 2005-10-10
I get no sound at all in DVDs.  I can play CDs, MP3s and I even hear linux sounds.  But DVD sound is missing in Totem.

Edit : I don't get sound from .avi or .mpeg, or any video for that matter :(

---

### Post by mokeyjoe on 2005-10-10
I can't play DVDs at all in Totem! Have you tried Xine? It works very well for me whatever I throw at it.

---

### Post by Velouria on 2005-10-10
How do I get the DVD to play in Xine, it autoplays in Totem and I can't get xine to open it up.

---

### Post by mokeyjoe on 2005-10-10
Maybe I'm not the best person to ask as I've currently got a problem where I can't get *anything* to autoplay or automount!

But this thread should help you. [http://www.ubuntuforums.org/showthread.php?t=69674]("http://www.ubuntuforums.org/showthread.php?t=69674")

---

### Post by mokeyjoe on 2005-10-10
Oh, and if you can't get DVDs to play at all in Xine you may need to go here:

[http://ubuntuguide.org/#dvdplayback]("http://ubuntuguide.org/#dvdplayback")

---

### Post by Velouria on 2005-10-10
I get playback in Xine, but still no sound for videos :(.  Please can anyone else help me?

---

### Post by Velouria on 2005-10-10
Bump

---

### Post by codejunkie on 2005-10-10
open synaptic and make sure you have installed these packages libdvdcss2, w32codecs, gstreamer0.8-plugins, gstreamer0.8-plugins-multiverse and totem-xine after that run ```
gst-register-0.8
``` and try your dvd in totem again it should be working.

---

### Post by Velouria on 2005-10-11
I'm missing the gstreamer multiverse plugins, where might I get those?

---

### Post by codejunkie on 2005-10-12
[quote=Velouria]I'm missing the gstreamer multiverse plugins, where might I get those?[/quote] you have to add extra repositories to your /etc/apt/sources.list file you can find help on that here [http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories").

---

