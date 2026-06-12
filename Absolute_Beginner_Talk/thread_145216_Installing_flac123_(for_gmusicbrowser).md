---
title: "Installing flac123 (for gmusicbrowser)"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by viviena on 2006-03-15
Hello all,

Though I'm accustomed to using Rhythmbox, I've recently been experimenting with [gmusicbrowser]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html") and am liking it a lot. However, though I'm currently getting mp3 playback with mpg321, I can't seem to get m4a playback working *with this particular program*. I assume flac123 should be what I need to get it working?

I followed the instructions in flac123-0.0.9.tar.gz to get it installed, and it seems to go smoothly except for this message when 'sudo make install':

> make[1]: Entering directory `/home/michelle/Desktop/flac123-0.0.9'
/bin/sh ./mkinstalldirs /usr/local/bin
  /usr/bin/install -c flac123 /usr/local/bin/flac123
make[1]: Nothing to be done for `install-data-am'.
make[1]: Leaving directory `/home/michelle/Desktop/flac123-0.0.9'

Not that I know much, but that seems to suggest to me that it's already installed. However, playback doesn't work. I've installed flac123-0.0.9-2_amd64.deb also, but again, nothing noticeable.

Does anybody have any ideas?

(If it helps, I'm running 64-bit Breezy.)

---

### Post by o_fortuna on 2006-03-15
[QUOTE=viviena]Hello all,

Though I'm accustomed to using Rhythmbox, I've recently been experimenting with [gmusicbrowser]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html") and am liking it a lot. However, though I'm currently getting mp3 playback with mpg321, I can't seem to get m4a playback working *with this particular program*. I assume flac123 should be what I need to get it working?

I followed the instructions in flac123-0.0.9.tar.gz to get it installed, and it seems to go smoothly except for this message when 'sudo make install':



Not that I know much, but that seems to suggest to me that it's already installed. However, playback doesn't work. I've installed flac123-0.0.9-2_amd64.deb also, but again, nothing noticeable.

Does anybody have any ideas?

(If it helps, I'm running 64-bit Breezy.)[/QUOTE]
flac123 is for listening to FLAC files (Free Lossless Audio Codec). Therefore, you need something else for M4A, namely FAAD. Try this in Applications-->Accessories-->Terminal (I don't know if this will work, but it's worth a shot):
```
sudo apt-get install gstreamer0.8-faad libgnome2-perl
```

---

### Post by viviena on 2006-03-15
Whoops, thanks for clearing that up! :) No luck though, as both already seem to be installed.

> gstreamer0.8-faad is already the newest version.
libgnome2-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I do have m4a playback in other programs such as Totem and Rhythmbox... or is gmusicplayer simply not capable of playing m4a files? (That's something I should probably have thought of beforehand.)

---

