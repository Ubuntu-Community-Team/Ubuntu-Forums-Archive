---
title: "Help with real player needed"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Cloudedbrains on 2007-05-25
Help since installing Ubuntu alone today I cant see any vidoes on [www.bbc.com](www.bbc.com) as I dont have real player (Or obviously windows media player either) !!

Ive seen guides on how to instal real player but they too complicated for me so has anyone got an idiots guide to it - simple step bu step guide !!

---

### Post by forestpixie on 2007-05-25
system - synaptic and search for real player - did it for me

:)

---

### Post by Cloudedbrains on 2007-05-25
Tried but it says "Xlibs not installed and is non-instable" :(

---

### Post by ugm6hr on 2007-05-25
> **Cloudedbrains said:**
> Help since installing Ubuntu alone today I cant see any vidoes on [www.bbc.com](www.bbc.com) as I dont have real player (Or obviously windows media player either) !!

Ive seen guides on how to instal real player but they too complicated for me so has anyone got an idiots guide to it - simple step bu step guide !!

Download this:
[http://www.mediafire.com/?bowej41bi4m](http://www.mediafire.com/?bowej41bi4m)

Then open it (double click from File Manager).  It should automatically open and install in GDebi.

I would recommend you then go to:
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
And Click on install now to get Media Player Connectivity which will allow you to define realplayer as default player for realmedia.

Interestingly, VLC media player can play windows media player files, although I haven't yet been able to get sound to work, so I stick to realplayer.

PS: This is for Feisty, since realplayer seems not to be in Synaptics for Feisty.

---

### Post by Cloudedbrains on 2007-05-25
Thankyou that worked to install it:)
Still have a problem though - it keeps telling me the link I want it too play is outdated ???

> Requested file not found. The link you followed may be outdated or inaccurate. (rtsp://wm-acl.bbc.co.uk/wms/news/media_acl/mps/fix/news/uk/video/96000/bb/96561_16x9_bb.wmv)

especially the embedded video on this site [http://news.bbc.co.uk/player/nol/newsid_6680000/newsid_6689200/6689267.stm?bw=bb&mp=wm](http://news.bbc.co.uk/player/nol/newsid_6680000/newsid_6689200/6689267.stm?bw=bb&mp=wm)

---

### Post by ampted on 2007-05-26
> **ugm6hr said:**
> Download this:
[http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb](http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb)

Then open it (double click from File Manager).  It should automatically open and install in GDebi.

I would recommend you then go to:
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
And Click on install now to get Media Player Connectivity which will allow you to define realplayer as default player for realmedia.

Interestingly, VLC media player can play windows media player files, although I haven't yet been able to get sound to work, so I stick to realplayer.

PS: This is for Feisty, since realplayer seems not to be in Synaptics for Feisty.

well to get VLC to worck only do dis!```
sudo apt-get install VLC
```

---

### Post by ampted on 2007-05-26
> **ampted said:**
> well to get VLC to work only do like here!```
sudo apt-get install VLC
```

but vlc wont work as a nett player! then u need a real player or windows media player!
You can try wine and install Iexplorer in there! I had some luck with a flash player but there are some sites that wont play media files on the flash! do 
wine! I just installed ubuntu 7.04 two weeks ago and there are some hacking but u will get there! just today I got battlefields to work (Norwegian not to god at English)

---

### Post by ugm6hr on 2007-05-26
> **Cloudedbrains said:**
> Thankyou that worked to install it:)
Still have a problem though - it keeps telling me the link I want it too play is outdated ???

especially the embedded video on this site [http://news.bbc.co.uk/player/nol/newsid_6680000/newsid_6689200/6689267.stm?bw=bb&mp=wm](http://news.bbc.co.uk/player/nol/newsid_6680000/newsid_6689200/6689267.stm?bw=bb&mp=wm)

Isn't this .wmv a Windows Media Player file?  Sent the news link so I can check it out on realplayer. 

As for VLC - I have it installed just fine thanks.  It's just Windows Media Files on bbc.co.uk seem to play on it without sound (on my system)..

---

### Post by Cloudedbrains on 2007-05-26
I dont want to install IE on wine but I do want to get it working on firefox !!
Other people I know have had issues with it too but got it working but since going Ubuntu alone mine wont work :(

---

### Post by Cloudedbrains on 2007-05-26
I don't know why or how but it has JUST started to work :(

---

### Post by ugm6hr on 2007-05-26
Try this:

[http://news.bbc.co.uk/player/nol/newsid_6680000/newsid_6689200/6689267.stm?bw=bb&mp=rm](http://news.bbc.co.uk/player/nol/newsid_6680000/newsid_6689200/6689267.stm?bw=bb&mp=rm)

You have set Windows Media Player format as default - rather than Realmedia.  Otherwise - from your link - click preferences in top right, and chose realplayer.

---

### Post by Cloudedbrains on 2007-05-26
As my last post said its fixed itself lol ;)

Will mark this as resolved :D

---

### Post by ampted on 2007-06-30
nice! a good thing are to cek ur firefox plugins!!! just update ur firefox

---

### Post by zhangweiwu on 2007-09-22
I don't know why. This keep happen to me. I install realplayer with this file:
> 
Download this:
[http://www.mediafire.com/?bowej41bi4m](http://www.mediafire.com/?bowej41bi4m)

Then open it (double click from File Manager). It should automatically open and install in GDebi.


And run reaplay from commandline, and get segment fault (core dumped).
Maybe I didn't install some needed components?

(Can we make life with Ubuntu easier? Using Linux on this particular area is so trouble-some, so many hours and a good part of my life is wasted to find out ways to access multimedia content that is available for windows for years. When you finally find out an ultimate solution, e.g. mplayer, there will soon be new situation where the ultimate solution doesn't solve..)

---

### Post by mali2297 on 2007-09-22
> **zhangweiwu said:**
> I don't know why. This keep happen to me. I install realplayer with this file:


And run reaplay from commandline, and get segment fault (core dumped).
Maybe I didn't install some needed components?

Try the solution given in this thread:
[http://ubuntuforums.org/showthread.php?p=3308600#post3308600](http://ubuntuforums.org/showthread.php?p=3308600#post3308600)
(post 26).

---

