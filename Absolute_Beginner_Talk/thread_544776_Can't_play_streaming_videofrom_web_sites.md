---
title: "Can't play streaming videofrom web sites"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-09-06
Hello


I'm trying to play streaming video from a number of web sites but nothing seems to work for me.

I downloaded the w32codecs and mplayer from Synaptic but nothing seems to work for me.

Can someone help me please?

Thank you!!!

---

### Post by apunc1 on 2007-09-06
have you tried vlc player?
it's in the repositories

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by greybirds on 2007-09-06
Use synaptic to install the package totem-mozilla. It's a plugin that lets the default media player for Ubuntu play videos in web pages. There is a similar plugin for mplayer but I can't seem to find its package name, and the totem plugin will download codecs for you automatically anyway.

---

### Post by parvinder on 2007-09-06
Hi, 
I'm also unable to play web streaming media (the sites that play streaming media in windows format).

I have installed mplayer, vlc, totem-mozilla, win32codecs, etc.....

But still, I can't play these streaming media... previously I use to get a black screen after installing all these now I get WHITE SCREEN.. that's the only difference....

---

### Post by SOULRiDER on 2007-09-06
Try installing mozilla-mplayer:
```
sudo aptitude install mozilla-mplayer
```

---

### Post by parvinder on 2007-09-06
Thanks for your quick reply.  But, I even had the mozilla-mplayer plugin installed but still the problem still persists....


I simply followed the instructions from here [https://help.ubuntu.com/7.04/musicvideophotos/C/onlinemedia.html#onlinemedia-plugins](https://help.ubuntu.com/7.04/musicvideophotos/C/onlinemedia.html#onlinemedia-plugins)
to install totem-xine and my issue got resolved.

Now I can play streaming windows media from web. But the Quality of the video is very bad you can hardly make out what is playing ( but some progress at least it plays)... Now need to work on to ensure that the quality is as good as we get while playing the same from Windows, which uses windows media player plugin for mozilla and IE.

---

### Post by andrew.46 on 2007-09-10
Hi,

 Saw your frustration:

> **lentomies said:**
> Hello
I'm trying to play streaming video from a number of web sites but nothing seems to work for me. downloaded the w32codecs and mplayer from Synaptic but nothing seems to work for me.Can someone help me please?Thank you!!!

 I use mplayer compiled from source + the 'all 2006 codecs' from the mplayer site. I would be curious to see an example video file that you cannot play. Can you give an address for one of these files so I can attempt to duplicate your efforts?

                  Andrew

---

### Post by lentomies on 2007-09-11
Hi Andrew!

Here are three sites I cannot hear nor see they are:

**MTV 3**

1. [http://www.mtv3.fi/](http://www.mtv3.fi/)
2. Click on "MTV3 Anytime Netti-TV". This link is found at the top middle of page.
3. When new window opens click on link "Uutiset" found at top left of page.
4. In the window to the left use the scrool bar to choose a news item to play."Kymmenen Uutiset", for example.


**Beeline TV.com**

URL: [http://beelinetv.com/](http://beelinetv.com/)

Here you can find media streams in 3 popular formats

1. Media
2. Real
3. Qtime

I would like to be able to view all three

[B]
Russian TV Online.com[/B]

URL: [http://russiantvonline.com/](http://russiantvonline.com/)

On the right margin you can see multiple "television" windows. I'd like to be able to play any of these.


I hope this helps you. Thank you!!!

---

### Post by skyjacker on 2007-09-11
I amtrying to get videos to play from Foxnews.com. I have tried every package listed in this post and nothing works.  Can anyone help?:mad:

---

### Post by philinux on 2007-09-11
i know its a work around and maybe gutsy will sort this out next month but another way is to get the extension mediaplayerconnectivity.

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

It just opens streaming stuff in a standalone player. I'd forgot about this but it works.

---

### Post by Detonate on 2007-09-11
> **skyjacker said:**
> I amtrying to get videos to play from Foxnews.com. I have tried every package listed in this post and nothing works.  Can anyone help?:mad:

Check this thread.

[http://ubuntuforums.org/showthread.php?t=374836](http://ubuntuforums.org/showthread.php?t=374836)

---

