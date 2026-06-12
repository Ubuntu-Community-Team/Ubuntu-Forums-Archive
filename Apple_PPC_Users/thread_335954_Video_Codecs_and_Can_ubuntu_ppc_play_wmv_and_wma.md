---
title: "Video Codecs and Can ubuntu ppc play wmv and wma?"
date: 2007-01-11
forum: Apple PPC Users
---

### Post by Kilopopo on 2007-01-11
Can Ubuntu PPC play wmv and wma? If so, what player can play those file formats?

what are the supported video codec in ubuntu ppc?

Sorry I am new to ubuntu I hope someone here can help me out.

thanks

---

### Post by linear on 2007-01-11
I don't think codecs for wma and wmv are available for PPC. You can read about what's possible [here]("https://help.ubuntu.com/community/RestrictedFormats") and [here]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs").

---

### Post by 3rdalbum on 2007-01-12
I believe VLC supports WMV 9, but I don't know if the version in the repositories has this support built-in.

Some files with the .wmv suffix are actually ASF video files, many of which will play on PowerPC. If you install the codecs as described on the first linked page in the post above, you should get the ability to play MPEG, DivX, many AVIs and all the free codecs as well. Flash Video (.flv) is serviced by VLC.

---

### Post by ubuntubrian on 2007-01-13
mplayer will play wmv and flv files as well as just about everything if you install the proper codecs which are on the mplayer website: [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
look for the binary codecs package for ppc. I installed mplayer from source as the ubuntu version wouldn't play wmv files and only played the sound on flash files without video. It's a bit weird as the source install puts files in different locations than the synaptic install. somehow my source version found the installed codecs and plays everything fine.

---

### Post by SyL on 2007-01-14
> **ubuntubrian said:**
> mplayer will play wmv and flv files as well as just about everything if you install the proper codecs which are on the mplayer website: [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
look for the binary codecs package for ppc. I installed mplayer from source as the ubuntu version wouldn't play wmv files and only played the sound on flash files without video. It's a bit weird as the source install puts files in different locations than the synaptic install. somehow my source version found the installed codecs and plays everything fine.
That right, mplayer is the answer!

---

