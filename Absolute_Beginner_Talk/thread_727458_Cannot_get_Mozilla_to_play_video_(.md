---
title: "Cannot get Mozilla to play video :("
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2008-03-17
Hi,
I have just installed ubuntu 7.10 and sorted the ATI graphics problems playing Compiz etc.

Anyway it was time to configure mozilla. I installed the flash player and youtube videos work fine.

The problem is getting the apple trailers to work.

I've tried everything from installing mplayer mozilla plugins, vlc player mozilla plugins and the ubuntu-restricted-extras and I still cannot get the apple trailers videos to work...

any thoughts please?

---

### Post by uberlube on 2008-03-17
Did you install flash?

---

### Post by uberlube on 2008-03-17
If not you can grab the tar.ga here and follow the instructions at the bottom to install. Cheers!
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by ROUBOS on 2008-03-17
flash works on mozilla
quick time movies that are used by [www.apple.com/trailers](www.apple.com/trailers) do not work

---

### Post by ROUBOS on 2008-03-17
did it... as i said before flash works... not quicktime

---

### Post by uberlube on 2008-03-17
Ya I know what you are talking about, I tried watching those Leopard previews to but no luck. I don't think they are viewable in Ubuntu. Proprietary BS.

---

### Post by uberlube on 2008-03-17
Check this out:

[http://heroinewarrior.com/quicktime.php3](http://heroinewarrior.com/quicktime.php3)

---

### Post by ROUBOS on 2008-03-17
last time i used ubuntu 7.04 i got them working ... cannot remember how... with mplayer plugin

---

### Post by Neo0351 on 2008-03-17
I just played one and it works on my computer, I did a quick search on synaptic for quicktime and it looks like there is library for quicktime, its called libquicktime1.  I would make sure you have it.  Are you running the 64 bit version or the 32 bit version?

---

### Post by ROUBOS on 2008-03-17
32 bit

libquicktime1 is installed

---

### Post by wolfen69 on 2008-03-17
works for me. as a matter of fact, all web content works. i uninstalled totem-mozilla (and everything else totem) and installed mozilla-mplayer and vlc. works everytime.

---

### Post by djbsteart1 on 2008-03-17
Have you looked in medibuntu, I think that there is quicktime support there, I know that there is lots of propietory codecs and stuff there.

---

### Post by Neo0351 on 2008-03-17
Check this thread out, I think it might help ya.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by ROUBOS on 2008-03-17
thanks people it works now :)

Just followed Neo0352's link above

thanks alot :)

---

### Post by aonegodman on 2008-03-22
Here's what worked for me. Short version.

After trying multiple suggested options with no luck - in Firefox 2.0.0.12 I went to

EDIT > Preferences > Content > File Types > Manage

Changed "QT  QT Video" from Use Quicktime Plug-in . . . . To Use Default Video Player.

In my case that was MPlayer. Went to [www.apple.com/trailers](www.apple.com/trailers) and it worked.

Maybe this will help someone else.   :lol:

---

