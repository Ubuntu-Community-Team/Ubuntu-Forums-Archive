---
title: "Gstreamer"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Zoolook on 2006-09-04
I notice from the restricted format quick start guide that Gstreamer 0.10 is important to install for the various codecs out there.

I'd like to know what each does though.  What's the difference between gstreamerx.x.x-bad and gstreamerx.x.x-nonlin and bad-do, base-d etc

---

### Post by croak77 on 2006-09-05
It's called 'bad' cause the quality of the plugins are not too great. 'ugly' is for plugins that may or may not be legal to distribute (aka mp3 support), 'good' are plugins that are legal to distribute and are good quality. Each set has different plugins, if you go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), you can search and look at the dependencies and tell what is included in each package.

---

### Post by Zoolook on 2006-09-05
I still have not managed to get either a QT movie or WMV version 9 or higher to run in Mozilla/Firefox or in the standalone Mplayer.

](*,)

---

### Post by nudnik on 2006-09-05
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Follow the directions found on the webpage listed above and you should have no more problems. After having installed Ubuntu on a number of machines I can almost configure the multimedia settings in my sleep, so beleive me, its not difficult at all once you get use to the repositories.

](*,)  << The Ubuntu Mascot  :mrgreen:

---

### Post by croak77 on 2006-09-05
Follow the link that nudnik posted. Mplayer does not use gstreamer.  For mplayer, you will need the w32codecs. They are not included by default cause they may or may not be legal in your country.

---

