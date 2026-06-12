---
title: "Playing embedded WMP files in FF"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by KeithO on 2005-10-11
A few web sites I visit have embedded videos that use Windows Media Player.  Firefox just shows an empty space and shows a link to get the plug in that returns nothing.  It leads to the Microsoft page for WMP which (surprise surprise) has no Linux version.  

How can I still use these web sites for video?

---

### Post by mpettitt on 2005-10-11
Short answer: you can't.
Long answer: if they are certain types of embedded media files, you can get FF extensions that give you a download link in place of the film. However, if they are streaming media, you are probably not going to be successful in this. The long term solution is to suggest to the site owners that they provide film in non-Windows Media formats.

Sorry...

---

### Post by Zelut on 2005-10-11
I've had trouble with embedded .wmv as well.  I know if you can download it or stream it (if they have a direct link to the .wmv someplace) you should be able to play it assuming you have the w32codec.  Other than that however I agree with mpettitt.  We've got to push these webmasters to stop making such proprietary non-standard formats.

---

### Post by KeithO on 2005-10-11
ok.  i went and found a FF extension that allows MPlayer to open externally however it crashes and throws error messages. 

1st, MPlayer interrupted by signal 11 in module: demux_open
2nd, - Mplayer crashed by bad usage of CPU/FPU/RAM. Recomiple MPlayer with --enable-debut and make a 'gdb' backtrace and disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash
3rd, -MPlayer crashed. This shouldn't happen. It can be abut in the MPlayer code _or_ in your drivers _or_ in your gcc version. If you think its MPlayers fault... blah blah blah
I see nothing about this kind of error in their documentation.

---

### Post by Tralobyte on 2005-10-11
In a terminal:
```

sudo apt-get install w32codecs mplayer-nogui mozilla-mplayer

```
EDIT: You may need to [add extra repositories]("http://ubuntuguide.org/#extrarepositories") before apt-get can install all of the packages listed above.

If you want the latest and greatest, follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=60505](http://ubuntuforums.org/showthread.php?t=60505)

---

