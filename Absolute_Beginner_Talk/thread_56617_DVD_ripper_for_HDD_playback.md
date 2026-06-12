---
title: "DVD ripper for HDD playback"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by mikeb on 2005-08-13
I've installed the DVD rip program recommended by the Ubuntu starters guide, but find that it seems designed to backup DVDs to CD, rather than allowing playback from the hard drive (it creates separate directories for each chapter in the DVD).

Does anyone know a program that will rip DVD to a format that is playable by xine, mplayer, totem or videolan?

---

### Post by sapo on 2005-08-13
Try vobcopy and dvdbackup

```
sudo apt-get install vobcopy dvdbackup
```

Should do the trick ;)

---

### Post by marsbt on 2005-08-13
dvdbackup will create VIDEO_TS and/or AUDIO_TS folders on your HDD. When done you can play the movie by using xine by the following command:
```
xine dvd:/home/username/path/to/VIDEO_TS
```

---

### Post by mikeb on 2005-08-13
[QUOTE=marsbt]dvdbackup will create VIDEO_TS and/or AUDIO_TS folders on your HDD. When done you can play the movie by using xine by the following command:
```
xine dvd:/home/username/path/to/VIDEO_TS
```[/QUOTE]
 Many thanks!!

---

### Post by nic2 on 2005-08-14
Another alternative is to right click the folder containing the ripped files and click on properties.  Select the 'Open With' tab and add 'xine'.  

When you now right click the folder the 'Open with "xine"' option will be available.  Clicking on this option will open the xine player and the movie will start playing.

---

### Post by wmcbrine on 2005-08-14
Here's another method I sometimes use:

mplayer -dumpstream -dumpfile movie.mpg dvd://1

This copies Title 1 to a single (huge) MPEG file. No menus, etc.

---

