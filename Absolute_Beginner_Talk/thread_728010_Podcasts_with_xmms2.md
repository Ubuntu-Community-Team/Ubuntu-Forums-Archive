---
title: "Podcasts with xmms2"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by abben on 2008-03-18
Hey, all. I want to get away from Rhythmbox for something ultra light weight, so am switching to xmms2.

I got this xmms2 plugin that is supposed to let me add podcaust urls, and have the program treat them as playlists:

[http://packages.debian.org/sid/xmms2-plugin-rss](http://packages.debian.org/sid/xmms2-plugin-rss)

So, if I want to add a podcast feed, I add it as an entire playlist. But their usage guide doesn't say anything about adding whole playlists:

[http://wiki.xmms2.xmms.se/index.php/Using_the_application](http://wiki.xmms2.xmms.se/index.php/Using_the_application)

Anyone else use xmms2?, or see something I'm missing?

---

### Post by kaivalagi on 2008-03-24
I'm new to xmms2 (installed today :) ).

Have you installed gxmms2, it's not great but it does have various playlist settings available...maybe that will help?

---

### Post by kaivalagi on 2008-03-30
I am successfully playing last.fm streams which can't be a whole lot different from podcasts. For this I run something like the following to play them:

xmms2 add lastfm://user/abben; xmms2 play

so I would expect for a podcast it would be something like:

xmms2 add <url>; xmms2 play

As far as I am aware this adds the stream to the existing playlist with whatever you already have there...

Hope that helps

---

