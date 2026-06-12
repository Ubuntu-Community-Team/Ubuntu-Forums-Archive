---
title: "&quot;Cannot read from source&quot;"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-11-03
DVDs aren't playing.  When I insert a DVD, it automounts it and opens Totem, spins for a second and then spits out that error message.  If I go to file -> play CD, it says that I don't have the proper codecs installed.  I've installed every Gstreamer package, including the one that plays DVDs.

I've also tried installing VLC, but when I try to open the DVD at the mount point (which is automounted at /media/cdrom0) it just sits there and does nothing.  

Anyone have any ideas?

---

### Post by justinmiller87 on 2007-11-03
Have you added the Medibuntu repository? If you haven't, follow the instructions on [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to do so. Then run the following from terminal to make sure you have everything:

sudo apt-get install ubuntu-restricted-extras libdvdcss2

I have an issue where if I open the disc from Totem it won't play, but if I load it into the player it will, so after you install those two try that and see if it will work.

---

### Post by TheOrangePeanut on 2007-11-03
Okay, I did all of that but I still get this error message:

Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

Any ideas?  I installed both ubuntu-restricted-extras and libdvdcss2, as well as another gstreamer package that was in medibuntu repos.

---

