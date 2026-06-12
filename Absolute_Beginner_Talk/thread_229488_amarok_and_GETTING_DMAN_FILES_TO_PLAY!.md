---
title: "amarok and GETTING DMAN FILES TO PLAY!"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by zanarkand100 on 2006-08-04
howdy :D so its my 2nd day on linux (woot)
and i love it appart from the damn installing lol can any1 tell me in straight forward ways tht a hedghog could how tro install codecs lol

also my friend has suggested i use amarok but i cant seem to find and info on the forums about it

any help would receive much love :D

Zan:KS

---

### Post by Tomosaur on 2006-08-04
I personally use Amarok, it's a very VERY good media player.

Don't worry about codecs and stuff like that, it's a common problem, and there are many many tutorials on here which will tell you the best ways to go about solving your problems. I personally spent ages messing around (since I like to mess about :P ) doing generally stupid things until stuff worked, so I'm probably not the best person to tell you how to sort this. However, if you just do a search using the box in the top right of the page, you'll find hundreds of threads about this exact problem.

---

### Post by T700 on 2006-08-04
Amarok is my favorite player, too.  I'd suggest using Automatix to take care of all your codec concerns.  See my sig for details.

Paul

---

### Post by patrick295767 on 2006-08-04
> **zanarkand100 said:**
> howdy :D so its my 2nd day on linux (woot)
and i love it appart from the damn installing lol can any1 tell me in straight forward ways tht a hedghog could how tro install codecs lol

also my friend has suggested i use amarok but i cant seem to find and info on the forums about it

any help would receive much love :D

Zan:KS

[http://www.ubuntuforums.org/showthread.php?t=160070&highlight=multimedia.sh](http://www.ubuntuforums.org/showthread.php?t=160070&highlight=multimedia.sh)

---

### Post by RudolfMDLT on 2006-08-04
Hi, this should help you sort out 99% of your Media troubles! Amarok is good, yes. When playing movies and DVD's, i find Totem or Mplayer the bests.

> Patent and licensing restrictions on media formats can complicate a free operating system's ability to distribute software that will support those formats.
- Quoted from the Ubuntu WIKI

Giving the wiki a read is always a good idea!:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

If you're new to Ubuntu, and you wish for a quick fix, this application is a solution to most of your media troubles! You would really do yourself some good by using Easy Ubuntu:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

It installs all of the codecs you need Plus the Firefox PlugIns for streaming media and the players needed for playing them and a whole lot of other things! It's a real winner!

Just one thing, there is a option for installing new graphics drivers. Like the saying goes, if it's not broken don't fix it! If you display works, UNTICK this option. Later when you are more comfortable with Ubuntu and the command line, then go messing around!

For WMV files get Mplayer and all the Mplayer addons for Firefox! Mplayer is brilliant when it comes to inline content

If you want to go it with the terminal:

Install the Xine streamer for gnome:
sudo apt-get install gxine

Install all the Windows codecs(Restricted ones! mp3, mp4, mov,wmv ect) that you're use to:
sudo apt-get install w32codecs

Then a good media player, Amarok:
sudo apt-get install amarok

If you have an IPod, you might need:
sudo apt-get install ipodslave

Inorder to play DVD's:
sudo apt-get install libdvdcss2

Hope this helps!

---

