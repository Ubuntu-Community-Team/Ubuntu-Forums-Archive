---
title: "Flash Player - Sound without Video.."
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Epperly on 2006-07-12
Hi, can anybody help me get video to work?
Also, with Windows Media I have tried to install the 32codecs but the file types still don't work.

I get like errors with everything I try to do :(

Can anyone help?
Thanks in advance.

---

### Post by Sef on 2006-07-18
To get Flash Player sound to work, follow the directions below.

In Gnome, Applications > Accessories > Terminal

In the terminal, type these two commands

sudo apt-get update

sudo aptitude install alsa-oss

---

### Post by Epperly on 2006-07-18
But now, say when I go to [www.streetfire.net](www.streetfire.net) and then videos, for some reason it says I still need to install flash player to play one of the movies. So, Idk what it is.

I've been using wine firefox, though and it's been working.

Thanks anyway I guess.

---

### Post by mattisking on 2006-07-19
Are you running Dapper? Which package did you install for flash? Give me a listing of the directory /usr/lib/firefox/plugins/

---

### Post by Epperly on 2006-07-19
I am running Dapper, and actually I don't remember where I installed flash from(I just saw flashplugin-nonfree, and that rings a bell as to being something I did).

Plugins:
flashplayer.xpt
libflashplayer.so
libjavaplugin.so
libtotem_mozilla.so
libtotem_mozilla.xpt
libunixprintplugin.so

---

### Post by richbarna on 2006-07-19
Automatix might be a good choice for you. It is a program that installs codecs, flash, etc automatically.
Take a look at my sig:
|
|
v

---

### Post by mattisking on 2006-07-19
yes indeed - Automatix isn't a bad choice. On the other hand, it appears like you have multiple versions of flash installed. I'd go into synaptic and do a search for "Flash". then I'd uninstall them if there are more than 1. Go back to that same directory and then see what's there. If these files remain:
flashplayer.xpt
libflashplayer.so

delete them (sudo rm flashplayer.xpt and sudo rm libflashplayer.so).

Then you can retry installing flashplugin-nonfree OR simply go to:
[http://www.macromedia.com/shockwave/welcome](http://www.macromedia.com/shockwave/welcome)

and you should get the pop-up for installing Firefox and just do it.

---

### Post by Epperly on 2006-07-19
When i search for flash in synaptic, it only shows "flashplugin-nonfree" and "libswfdec0.3" to be checked off.

If I remove nonfree should I then install from macromedia.com or the automatix thing?

---

### Post by Epperly on 2006-07-19
Aight I'm giving Automatix a try, looks pretty cool thus far(installed).

[edit]ugggh, I tried installing via automatix and it didn't seem to work(example when I go to streetfire.net click videos and try and play one, it gives me the install flash player shit again[/edit]

---

