---
title: "MP3 and WMA"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by SonAsylum on 2006-03-02
Some one posted earlier that you could get MP3 and wma suport in Ubuntu by geting these things: gstreamer0.8-lame, liblame0, lame and w32codecs package. None of them however are showing up in Synaptic is there another way of getting them?

---

### Post by andrewsawyer on 2006-03-02
Lame should be there.  Have you removed all the #'s from the start of links in /etc/apt/sources.list yet?

I know w32codecs is not in the repos, however if you do a search in google you should be able to find an Ubuntu compiled deb file that you can install.

---

### Post by viviena on 2006-03-02
Do you have the universe and multiverse repositories enabled? They're not on by default, and they're probably where your packages are lurking (I know lame's in Multiverse, at least). See [AddingRepositoriesHowTo]("https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show") to find out how to enable them. Once that's done, try searching Synaptic again for your packages. :)

Edit: Whoops! Not quick enough...

---

### Post by SonAsylum on 2006-03-02
I enabled that univers and multiverse and everything but i still can't find any of them

---

### Post by Madpilot on 2006-03-02
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) should help w/ w32codecs & other multimedia stuff.

---

