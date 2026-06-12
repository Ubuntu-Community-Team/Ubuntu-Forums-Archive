---
title: "[SOLVED] Moving files from folders to one location"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-10-09
I download a number of podcasts using Icepodder. Individual directories are set up for each.

I want to move the files into one directory so I can copy them en masse to mp3 player. So far, I have been doing this by a mv script stating the full directory paths each time. This works, but every time I subscribe to a new podcast I need to do a new script - I'd rather have one that finds them all.

And that seems to be part of the cure - find.

```
find /media/hdb1/My\ Music/Podcasts -name *mp3
``` will happily list them all (they are on my windows drive)

But if I try:

```
mv `find /media/hdb1/My\ Music/Podcasts -name *mp3` `/media/hdb1/My\ Music/Podcasts/`
```

I run foul of spaces in the names of the individual podcast directories (which of course, I can't change, as they will only be changed again when new podcasts come along for that series) and get something like this:

```
bash: /media/hdb1/My Music/Podcasts/: is a directory
mv: target `Unlimited/hoggart290307.mp3' is not a directory
```

and if I try:
```

 mv `find /media/hdb1/My\ Music/Podcasts -name *mp3` /media/hdb1/My\ Music/Podcasts
```

I get:

```
mv: cannot stat `Guardian': No such file or directory
mv: cannot stat `Unlimited/hoggart290307.mp3': No such file or directory
```, etc

So, I'm nearly there! Can someone help me overcome the last obstacle please?!

Thanks!

---

### Post by Scunizi on 2007-10-09
Why move them to one directory when you could use .. say .. Amorak, mount your MP3 player and just tag what you want transferred and hit go?

Not sure how to write this script but you could search for mp3 recursively in your podcast directory and pass the rusults to copy them to your mp3's mount point and directory.  It'll save the extra step.

---

### Post by qprfact on 2007-10-12
This solved it:

find ./ -name '*.mp3' | while read FILE

do

   mv "$FILE" <destination>

done

---

