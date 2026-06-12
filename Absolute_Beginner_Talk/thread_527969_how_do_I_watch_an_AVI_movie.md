---
title: "how do I watch an AVI movie?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by tobyfountain on 2007-08-17
Hi,
I have tried instaling various things from add/remove to enable it, but it still doesn't work.

please can someone tell me how to easily install the right things to watch AVI movies.

Please either tell me what to type in terminal if possible (and easy) or another way you think is easier.

Thanks everyone.

toby fountain

---

### Post by Dark Star on 2007-08-17
Try installing VLC.
```
sudo apt-get install vlc
``` this will ease the use :) btw my Movie Player can run .avi files :D

---

### Post by tobyfountain on 2007-08-17
ive done that, but it still does not work.

the video is not playing, but i can hear the sound.

any ideas?

thanks

---

### Post by Hobo Joe on 2007-08-17
Do you hear sound in any other player? Or any other formats in that certain player?

---

### Post by phenest on 2007-08-17
Then it is not a standard AVI, but a DViX AVI. You need an appropriate codec to play it.
Try this:
```
sudo apt-get install gstreamer0.10-ffmepg
```
You may have to enable some repositories for it to install.

---

### Post by limberlegs on 2007-08-17
Just off the top of my head, do you have the proper codecs installed?  I'm not at my desktop right now, and thus cannot check this for sure, but try going to add/remove, and search for gstreamer.  One of these should provide you with the proper AVI codec.

EDIT: you beat me to it :( and it was the first time I've been able to actually help someone (I'm still mostly a noob).

---

### Post by tobyfountain on 2007-08-17
ok, ive done all of those.

same problem though.

is there a version of divx for linux?

if so, how do i get it?


thanks

---

### Post by phenest on 2007-08-17
Yeah, you just installed it. Are you using Feisty? If so, opening a video file in Movie Player should give a prompt for downloading necessary codecs.

---

### Post by phenest on 2007-08-17
Ok. These are the packages you need to play any type of video.
```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
```

---

### Post by mysticmatrix on 2007-08-17
Are you running Beryl or COmpiz fusion along with trying to watch a video? If yes see if problem persists even after you switch off Compositing.

---

### Post by tobyfountain on 2007-08-17
it was the compiz one!!

Thanks very much!!!


Toby Fountain

---

### Post by mysticmatrix on 2007-08-17
> **tobyfountain said:**
> it was the compiz one!!

Thanks very much!!!


Toby Fountain

If you could tell us what graphics card you use, we might be able to suggest you ways to watch videos while Compositing is on.

---

### Post by lennydizzy on 2008-05-01
I am using Nvidia 8800 GT, after switch from compiz to metacity, the movie playback problem is sloved.

Can you plz suggest how to play movie while using compiz?

---

### Post by lennydizzy on 2008-05-01
actually the problem is the flash plugin, the nonfree flash has no sound if i open a movie first. The totem is slow and no sound if I open a flash site first. Maybe a sound mixer ALSA kind of problem?

---

