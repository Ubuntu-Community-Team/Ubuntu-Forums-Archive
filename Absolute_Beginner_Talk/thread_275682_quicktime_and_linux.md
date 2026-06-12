---
title: "quicktime and linux?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by y3ahright on 2006-10-11
ok i want to watch a quicktime movie over the internet ([http://www.charlotteskate.com/videos.htm]("http://www.charlotteskate.com/videos.htm")) 
but it is telling me i have a missing plug-in and i try to install but it says manually and when i click that nothing happens.  I tryed saving it and using VLC but it came out blurry.  So is there a way i can get some kind of plug-in so i can watch quicktime on the internet????

---

### Post by John.Michael.Kane on 2006-10-11
This may help
[DOCS/codecs-status]("http://www.mplayerhq.hu/DOCS/codecs-status.html")
[Binary Codec Packages]("http://www.mplayerhq.hu/homepage/design7/dload.html")
[Quicktime/Linux]("http://www.infoanarchy.org/en/Real_Media/Linux")


I have not tested mplayer,however. it does offer quicktime support..

---

### Post by y3ahright on 2006-10-11
ok but do these allow me to watch the video without saving it to my desktop?

---

### Post by Sweet Spot on 2006-10-11
Assuming you're using Firefox, install an extension called mediaplayer connectivity. It will allow playback of all embedded video from Quicktime, Real Media and WMP. There's a quick wizard install process, and all you have to do is choose the player you want to open the files. I just chose to use Totem player, since it's what I use for all my video anyway. 

Doug

---

### Post by Delkster on 2006-10-11
It's also possible to just install the Totem Firefox plugin (if you use GNOME) and hopefully have the videos show up correctly directly on the website. It doesn't always work flawlessly, though.

The package is totem-gstreamer-firefox-plugin for Totem using the Gstreamer engine (which is installed by default), or totem-xine-firefox-plugin if you've installed Totem with the Xine engine (which is what I'd probably recommend).

You'll probably also need to have some extra codecs installed if you don't have them already, but if you do, all you should need is a browser plugin if you want to view the videos without downloading them as files first.

---

### Post by guysmiley25 on 2006-10-11
I used mplayer, I went to that site and it worked for me.

I have firefox, mplayer and mozilla-mplayer. So if you already using firefox adn you want to use mplayer then you want.

```
$ sudo apt-get install mplayer mozilla-mplayer
```

Or if you already have mplayer
```
$ sudo apt-get install mozilla-mplayer
```

I think thats all you need cause i have not installed any otehr codecs or anything like that.

Let me know how you get on

---

### Post by Howlin' Hobbit on 2006-10-13
> **guysmiley25 said:**
> ... if you already using firefox adn you want to use mplayer then you want.

```
$ sudo apt-get install mplayer mozilla-mplayer
```

I just used that code and bingo! I went to my favorite video site (Midnight Ukulele Disco -- [www.ukuleledisco.com](www.ukuleledisco.com)) and was watching the vids again.

It pops open in it's own window rather than "staying put" but that doesn't bother me much. Better yet, MUD has recently done a redesign of the site and, for whatever perverse reason, the programmer left off the controls for the video plugin. This means that you can't stop the playback and let the whole thing load... you *have to* stream.

With this plugin you the controls are there and those of us with the lower bandwidth can still enjoy the vids.

> **guysmiley25 said:**
> Let me know how you get on
Just fine! Thanks much for the help!

---

### Post by guysmiley25 on 2006-10-21
Glad to help. anything to make sure people are using linux and not that other thing I don't like to mention named after those square things you use to look outside. Winblows is it?

---

### Post by jamaas on 2006-11-21
Thanks Doug, Cool!

Jim

> **Sweet Spot said:**
> Assuming you're using Firefox, install an extension called mediaplayer connectivity. It will allow playback of all embedded video from Quicktime, Real Media and WMP. There's a quick wizard install process, and all you have to do is choose the player you want to open the files. I just chose to use Totem player, since it's what I use for all my video anyway. 

Doug

---

