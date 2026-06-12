---
title: "usb device busy?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by angelsneverdie on 2007-12-16
when i switch amarok to alsa, and type "usb-audio" in the stereo device field, and press play it just runs through the playlist track names (quickly, without playing) and then gives me the error.:

Audio output unavailable; the device is busy.
xine parameters:


note that there is nothing after xine parameters:

some history of my probleM:  i'm trying to get logitech music anywhere thingy (bluetooth/usb audio transmitter) working on gutsy.  i've followed the instructions on this post:  [http://ubuntuforums.org/showthread.php?p=3958560#post3958560](http://ubuntuforums.org/showthread.php?p=3958560#post3958560)
but can't get it to work and can't get a response on that post.

i'm trying to get this figured out because i only have 20 days left to return the logitech device - really wish li could get this working.  anyone have any ideas?  it would be greatly appreciated

---

### Post by coolbrook on 2007-12-16
I was getting this error after I upgraded to Gutsy and before I switched to *Autodetect* for my playback.

System..Preferences..Sound.

---

### Post by angelsneverdie on 2007-12-16
my system playback is indeed set to autodetect.. but i tried setting it to usb-audio and it played the test sound . . . now i just need to figure out why armarok won't work.
thanks for your suggestion . . . anyone know anything else i might try?

---

### Post by smallrock on 2008-01-02
I got Logitech Music Anywhere working on Ubuntu Edgy 6.10 on my laptop with GXINE although it didn't work on Amarok (Amarok said "the device is busy"). I wrote the soundcr script to /etc/ as was instructed on the forum, and just plugged the USB dongle and played music with GXINE and it worked ok with it. Weird, but got it working.

---

