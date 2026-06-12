---
title: "real player and w32"
date: 2006-07-14
forum: Apple PPC Users
---

### Post by Manoau2002 on 2006-07-14
Is it possible to install real player and w32 codecs on a mac ibook. The files I have seen in the wiki on other websites are for intel based computers only (ex. realplayer(i386).deb)

 If this is not possible is there a program that can play real player files (rmvb) on mac ibooks.

---

### Post by wieman01 on 2006-07-14
If you are using Dapper, then this link may work;

[http://www.ehomeupgrade.com/entry/2663/how-to_get_full]("http://www.ehomeupgrade.com/entry/2663/how-to_get_full")

Convenient way of turning your Linux-PC into a Media Center.

---

### Post by digs on 2006-07-15
An experimental Real for linux/ppc is available at:

[https://player.helixcommunity.org/2005/downloads/]("https://player.helixcommunity.org/2005/downloads/")

VLC/mplayer handles up to WMV2 (aka 'Windows Media Video 8') and both are in the repositories. The WMV3 hack "(aka 'Windows Media Video 9') is only available for x86.

---

### Post by calum on 2006-07-15
> **Manoau2002 said:**
> Is it possible to install real player and w32 codecs on a mac ibook. The files I have seen in the wiki on other websites are for intel based computers only (ex. realplayer(i386).deb)

 If this is not possible is there a program that can play real player files (rmvb) on mac ibooks.

RealPlayer (and HelixPlayer) for PowerPC Linux is downloadable here: [https://helixcommunity.org/project/showfiles.php?group_id=154]("https://helixcommunity.org/project/showfiles.php?group_id=154").  Several users (including me) have reported problems with streaming video, though.

---

### Post by 3rdalbum on 2006-07-16
It's not just streaming video - Realplayer PPC just flat-out doesn't work for most people.

W32codecs, for all intents and purposes, doesn't work unless your computer has an x86 processor. Having said that, I suppose it might be possile to get user-mode emulation working on QEmu, and run MPlayer and the w32codecs on that? Don't ask me how!

---

### Post by calum on 2006-07-16
> **3rdalbum said:**
> It's not just streaming video - Realplayer PPC just flat-out doesn't work for most people.

Fair enough... works fine on my G4 PowerBook, apart from the video.  (Actually, it worked perfectly in Ubuntu Breezy, and the only thing that has changed since then is Ubuntu, so I'm guessing it's not entirely RealPlayer's fault anyway.)

---

### Post by Ububurns on 2006-08-07
Seems nobody has got around to compiling ffmpeg on PPC with wmv3 decoding ability - except for me...

If you would like it, I guess I can email it to you (it may be illegal to host it online) as it's only a 3MB executable. Let me know if you would like it!

It's not particularly fast, but you can use it to convert your wmv3 files to avi or mpeg or whatever, for playback.

---

