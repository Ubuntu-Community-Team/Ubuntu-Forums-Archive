---
title: "Radio on linux?"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-11
Hello im trying to listen to radio over the internet i guess im "stramin" but it onlu has options for winamp and some other program... how do i use this streaming services on linux ubuntu? 

Is there an winamp functional look-a-like and please post the install moments to meaning how to`s :)

---

### Post by ron999 on 2006-09-11
Hi haxer
The Winamp lookalike is XMMS player, you can get it with Synaptic.

---

### Post by Shay Stephens on 2006-09-11
I listen (using firefox) to radio stations that have "listen live" links.  The way I got it working was to install two packages via the terminal:

```
sudo apt-get -y install mplayer
sudo apt-get -y install mozilla-mplayer
```

---

### Post by bodhi.zazen on 2006-09-11
> **haxer said:**
> Hello im trying to listen to radio over the internet i guess im "stramin" but it onlu has options for winamp and some other program... how do i use this streaming services on linux ubuntu? 

Is there an winamp functional look-a-like and please post the install moments to meaning how to`s :)

Install streamtuner
[Streamtuner](http://www.nongnu.org/streamtuner/)

Just ```
aptitude install streamtuner
``` or use synaptic. Works with any player, I use xmms.

---

### Post by Fedz on 2006-09-11
XMMS Music Player- from System > Admin > Synaptic Package Manager.

Some great XMMS themes from [Gnome-Look.org > XMMS Themes](http://www.gnome-look.org/index.php?xcontentmode=130)

*Note: XMMS skins folder is in Places > Home. Then goto View > show hidden files (Ctrl+H) and then into **.**XMMS > Skins*

Kind regards

---

### Post by haxer on 2006-09-11
Hmmm.. i installed streamtuner but how to use it?

---

### Post by haxer on 2006-09-11
Omg totally love this place it worked i donwloaded the .pls file on the radio internet site then i just opened it with xmms really great thanks to all you out there ;)

---

### Post by bodhi.zazen on 2006-09-11
> **haxer said:**
> Hmmm.. i installed streamtuner but how to use it?

Hmmm..Should be in your menu.

If not type```
streamtuner &
```in a terminal.

I see you have xmms up and running. 8)

---

### Post by Fedz on 2006-09-11
Pleased to learn you got sorted with ease.

Streamtuner is good if you don't want to hunt the net for radio stations as they are gathered within the software panel.

Out of personal preference I like XMMS ... as I just goto shoutcast :)

---

### Post by haxer on 2006-09-11
Thank you all love this forum keep on answering questions and maybe in a year or two ill be like you guys i love tux and linus to for doing this exellent os :)

---

