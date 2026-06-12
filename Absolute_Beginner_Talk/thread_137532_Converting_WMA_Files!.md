---
title: "Converting WMA Files!"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by Leo_01 on 2006-02-28
Going to kick myself in the butt!
I currently plan to move all my music files to Ubuntu but i noticed that some of my music files is in WMA format!
Is there a way to convert them to other formats?

---

### Post by AndyCooll on 2006-02-28
You shouldn't need to convert your wma files to play them on Ubuntu. You simply need to install the w32codecs and they'll play using one of the range of Linux media players.

Easiest way to get the relevent codecs is to use Autmatix, that'll sort everything out for you.

:cool:

---

### Post by frodon on 2006-02-28
I suggest you this really good script : [http://www.ubuntuforums.org/showthread.php?t=82806](http://www.ubuntuforums.org/showthread.php?t=82806)

---

### Post by xmastree on 2006-02-28
[QUOTE=Leo_01]Going to kick myself in the butt!
I currently plan to move all my music files to Ubuntu but i noticed that some of my music files is in WMA format!
Is there a way to convert them to other formats?[/QUOTE]

Here's a nautilus script I use for that. It converts wma to ogg.

```
for arg; do
# Rip with Mplayer / encode with Oggenc
mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$arg" && oggenc -q 6 audiodump.wav -o "$arg";
# Convert file names
mv "$arg" "`basename "$arg" .wma`.ogg"
# cleanup
rm audiodump.wav
done

```

Save that to a file in ~/.gnome2/nautilus-scripts (make that directory if you dont' have it), make the file executable, then if you right-click on a wma file (or a bunch of files) it will re-encode it (or them).

You need mplayer and vorbis-tools installed.

(thanks to the original author of this script, who's name escapes me)

---

