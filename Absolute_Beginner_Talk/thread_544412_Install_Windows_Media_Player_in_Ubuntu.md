---
title: "Install Windows Media Player in Ubuntu"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by pate4ever on 2007-09-06
Hello Everyone - 
    I have recently started pharmacy school at a major university. The lectures are primarily delivered on-line in using a format that is pretty bizarre. I have been told that this format is **only** compatible with Windows Media Player. I believe the streaming video file is a .css extension. The company that produces the video is named "Digiscript" this is the website: [http://www.digiscript.com/]("http://www.digiscript.com/"). Is there anyway I could get the codecs for this file type? Barring that, is there any way I could install windows media player in ubuntu?

**Also: I have noticed this forum which describes my problem (which is similar), yet has gotten no replies
[http://ubuntuforums.org/showthread.php?t=148375]("http://ubuntuforums.org/showthread.php?t=148375")

Thanks - pate

---

### Post by WebSiteGuru on 2007-09-06
Try this thread and see if that helps.

[http://ubuntuforums.org/showthread.php?t=524042](http://ubuntuforums.org/showthread.php?t=524042)

---

### Post by FuturePilot on 2007-09-06
You might want to look here
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
If you have the proper codecs installed you should be able to play it.

---

### Post by n3tfury on 2007-09-06
i don't really have an answer for you, but an alternative.  if you have enough RAM you could install [[COLOR="DarkOrange"]Virtualbox[/COLOR]]("http://www.virtualbox.org/") and run XP in that environment so you could use WMP.  just a thought.

---

### Post by trippinnik on 2007-09-06
Well I checked it out.  I've got the typical set of restricted formats codecs installed, the ones other guys already posted links on how to install, and it works.  I have had varying success using differenct plugins for the browser so you may have to experiment between vlc, mplayer-plug and totem-xine plugin.

---

### Post by pate4ever on 2007-09-07
I have tried other media players, VLC, totem, etc. None of them play the .css extension. So if I run a virtualization does that mean I have to install windows and run it through linux? I don't want to buy windows as I do not have the money.

---

### Post by avik on 2007-09-07
> **pate4ever said:**
> Hello Everyone - 
    I have recently started pharmacy school at a major university. The lectures are primarily delivered on-line in using a format that is pretty bizarre. I have been told that this format is **only** compatible with Windows Media Player. I believe the streaming video file is a .css extension. The company that produces the video is named "Digiscript" this is the website: [http://www.digiscript.com/]("http://www.digiscript.com/"). Is there anyway I could get the codecs for this file type? Barring that, is there any way I could install windows media player in ubuntu?

Are you sure the .css file is a media file.  A CSS file describes how a web page looks, and you never actually have to look at it.

Also, at the digiscript site, I was able to view the demo fine, though that was in flash.  Another demo linked from the Product Tour page was not in flash, but I could see the video just fine.  Unfortunately, I got no audio.

---

### Post by RomeReactor on 2007-09-07
> **avik said:**
> Another demo linked from the Product Tour page was not in flash, but I could see the video just fine.  Unfortunately, I got no audio.

Same here. The file is a wmv, though I couldn't get audio either with totem or mplayer; here's the url of the video at 100 Kb:
```
mms://a532.v103061.c10306.g.vm.akamaistream.net/7/532/10306/v8/digiscript.download.akamai.com/3140/a/9000/9198/9198-100k.wmv?obj=v8&WMStartupProfile=0
```

---

### Post by -SpaZ on 2007-09-07
> **RomeReactor said:**
> Same here. The file is a wmv, though I couldn't get audio either with totem or mplayer; here's the url of the video at 100 Kb:
```
mms://a532.v103061.c10306.g.vm.akamaistream.net/7/532/10306/v8/digiscript.download.akamai.com/3140/a/9000/9198/9198-100k.wmv?obj=v8&WMStartupProfile=0
```

Have you tryed VLC?  It can play pretty much anything as long as you have the proper codecs installed.

---

### Post by RomeReactor on 2007-09-07
> **-SpaZ said:**
> Have you tryed VLC?  It can play pretty much anything as long as you have the proper codecs installed.

Well, it's been ages since I last used VLC, but I don't think lack of codecs is the issue in my case, as that's one of the very first things I enable on a fresh install: since I installed Feisty, this is the first wmv file I've had trouble playing (video plays fine, although without sound--video codec is wmv9, audio codec unknown).

However, this particular video is found in the tour section of the digiscript site mentioned by pate4ever, and what he's having trouble with is that "...the streaming video file is a .css extension", according to his first post. I suspect the file is embedded in a pop up window, and what he's trying to play is the link/button for that window. I could certainly be wrong; we'll just have to wait for a reply from him.

---

### Post by philinux on 2007-09-07
just tried the intro and it was flash and played fine.
mplayer plays their other stuff too

---

### Post by Paul133 on 2007-09-07
You've installed w32codecs?

---

### Post by pate4ever on 2007-10-29
Hey everyone. If there is still anyone out there that is reading this ... I got the video portion of the videos to play fine in VLC finally. The audio does not work. The file selection is a .css file I believe. The address starts with mms://

How would I go about installing all audio codecs possible? 

Thank you!

---

