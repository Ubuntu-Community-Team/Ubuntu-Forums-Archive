---
title: "snes9x on ps3"
date: 2007-02-07
forum: Apple PPC Users
---

### Post by mb26 on 2007-02-07
hello.
i'm trying to get snes9x to work on my ps3. i have tried installing it via synaptic package manager, and the (presumably) executable is in /usr/bin
but nothing happens when i click it to open. (nor does it appear on the applications menu).

i tried looking for the 'required' stuff from here;
[http://rpmfind.net/linux/RPM/freshrpms/yellowdog/4.0/snes9x/snes9x-1.43-0.0.yd4.fr.ppc.html](http://rpmfind.net/linux/RPM/freshrpms/yellowdog/4.0/snes9x/snes9x-1.43-0.0.yd4.fr.ppc.html)
with the SPM, (and universe and multiverse selected), but i couldn't find the first one (as far as i got).

what should i be doing??

[[EDIT]] sorry, figured it out.
u need to install gsnes9x also for gnome..

---

### Post by Ciego on 2007-02-07
You do not need to use gsnes9x.

You can run a game like this from the terminal
```
 $ snes9x -sound /path/to/your/legally/obtained/rom
```

---

### Post by jesus5511 on 2007-02-07
Sorry to intrude in the thread, but is Ubuntu actually decent to use on PS3?

---

### Post by mb26 on 2007-02-08
yeah, not bad.
a few issues:
-no gfx card support yet, so no 3d games (who cares, u have a ps3 for that)
-no adobe flash for PPC linux (atleast u can save videos from sites like utube with 'video downloader' extension for FF and view with VLC) <- looking for a streaming alternative.. also perhaps u can use wine or something to get flash?? [idk?]
-sound is a bit 'maybe' at the moment-- someone has said it works for them out of the box, but not me. i'm sure it should be easily fixable by someone with the knowhow as it works fine with YDL.

If u have a CRT TV then overscan is an issue- either have ~1inch of black border round your screen, or select 'full screen' and lose ~1inch of the desktop (ie, bigger than viewable screen).
i'm hoping that there will be some program (or somehow) that will allow the ubuntu desktop to be restrained to the viewable area of my screen! also interlaced is fairly annoying for text if ur tv only supports that.

the main reason i wanted it was to play all types of video and audio, from everywhere, on my TV. firefox (even w/o flash) is also wayy better than the ps3 browser. and i'm kind of getting used to using the a 'pc' in the lounge.

The (IIRC) 192mb of ram hasn't really been a restriction yet.. and whilst the hdd is smallish u can always use an external one or upgrade the one in there. or just use network shares.

Other than all that, its pretty much like on a PC..

[EDIT: sound sorted i think. works for me. [[click]](http://ubuntuforums.org/showthread.php?t=343113). its pretty sweet.]

---

### Post by Ciego on 2007-02-08
> **mb26 said:**
> 

If u have a CRT TV then overscan is an issue- either have ~1inch of black border round your screen, or select 'full screen' and lose ~1inch of the desktop (ie, bigger than viewable screen).


It seems that this is not only a problem with CRT TVs because the same thing happens on my 1080p HDTV.  It doesn't make as much of a difference because the black border doesn't really take up that much space on my TV although it would be nice to use the whole thing.

---

### Post by mb26 on 2007-02-08
well what happens when u chose full screen mode though? i would have thought that would fit perfectly on an LCD/plasma ??

---

### Post by Ciego on 2007-02-08
> **mb26 said:**
> well what happens when u chose full screen mode though? i would have thought that would fit perfectly on an LCD/plasma ??
I thought the same thing but when I tried it full screen, it did the same as my CRT and cut off the edges.  I couldn't even see the panels on the top or bottom.

---

