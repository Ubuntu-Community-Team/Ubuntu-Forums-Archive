---
title: "mp3's on OSX partition to KDE"
date: 2006-04-21
forum: Apple PPC Users
---

### Post by Rxke on 2006-04-21
Hi, 
I've been using Gnome for quite awhile on my laptop, but want to try KDE on my tower. (I used KDE years ago under Debian, and grew quite fond of it after awhile, curious how it has evolved since then)

One thing I want to do is to keep my iTunes collection, which resides on a separate harddisk (Hfs+ formatted)  and play the files through KDE.

Is this possible? And which player is the preferred one in KDE?

---

### Post by stuporglue on 2006-04-21
> One thing I want to do is to keep my iTunes collection, which resides on a separate harddisk (Hfs+ formatted) and play the files through KDE.

Sure. Add a line for it in fstab with type =  hfsplus, options = defaults (I think). The last two options should be 0 0 so it doesn't get fsckd. 

> Is this possible? And which player is the preferred one in KDE? 

I like Amarok. Don't forget you'll need codecs for the mp3s, and you won't be able to play your encrypted bought-in-iTunes songs!

---

### Post by Rxke on 2006-04-21
Thanks! 

Yes I knew about the codecs; and all my mp3's are from my own CD's, never thought the commercially available 128kbs were worth listening to/paying for  ;)
(wonder what'll happen to the few aac's I have encoded, grin)

---

### Post by stuporglue on 2006-04-21
> (wonder what'll happen to the few aac's I have encoded, grin)

You can play them, as long as they're not encrypted. I forget which codec you need, maybe gstreamer*aa ?

---

