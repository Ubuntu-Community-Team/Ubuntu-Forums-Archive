---
title: "how do I fix this mplayer playback problem?"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-10-31
won't play any video but will play music types.

see attachment for visual.

is there something I can do in terminal? maybe fix its config file?

---

### Post by dbd on 2006-10-31
Hmm, you could try changing the video driver mplayer is using. Go to the Video section of mplayer's preferences, change the driver and then restart to see if it works.

I'm assuming your have all the codecs installed mentioned here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Perfect Storm on 2006-10-31
Try change it to X11/XV

---

### Post by maddbaron on 2006-10-31
same problem...changed what you said...could be the codecs? in installed them through automatix2

---

### Post by dbd on 2006-11-01
I don't know if it could be the codecs or not (don't know what the error message means!) but you might as well check, do u have everything installed that is listed here?:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Maybe automatrix missed something.

---

### Post by DeadEyes on 2006-11-01
I had the same problem fixed it by changing vo_driver
[http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2541340](http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2541340)

Running: 
$mplayer -vo help

Gave me a load of options I just picked ones and random and they worked try X11 or gl2

---

### Post by maddbaron on 2006-11-01
THANKS I had to switch to win32 codecs and switch the sound around then enable x11 ximage and it works now! thanks for the help!

---

