---
title: "can't play mp3 songs"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by SOCK0001 on 2006-09-23
guys i just switched from windows to linux .... how do i play mp3 songs do i need special software for dat?????

thank you

---

### Post by krazed nun on 2006-09-24
you can use XMMS. Its an awesome program. Just search 'XMMS' in synaptic package manager.:D

---

### Post by koshari on 2006-09-24
what program do you want to use to play mp3,s?

as they all depend on different packages, ie, in amarok you will need xine extra codecs, 

or others you may need gstreamer bad/ugly packages or lame.

 these are available in the multiverse or universe repositorys that are dot enabled by default.

---

### Post by james_san on 2006-09-24
Well you should look at this page:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

It has some great information on how to install mp3 and other codecs for ubuntu.

Basically, for mp3 support, you need to install the package called 'gstreamer0.10-plugins-ugly', which can be found in Synaptic Package Manager (which is in the System->Admin menu)

---

### Post by RudolfMDLT on 2006-09-24
Hi, this should help you sort out 99% of your Media troubles. Amarok is a good player. When playing movies and DVD's, i find Totem or Mplayer the best. Mplayer is the best for WMV format.

Quote:
Patent and licensing restrictions on media formats can complicate a free operating system's ability to distribute software that will support those formats.
- Quoted from the Ubuntu WIKI

Giving the wiki a read is a good idea:
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

You're new to Ubuntu, this application is has solutiona to most of your media troubles! You would really do yourself some good by using Easy Ubuntu:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

It installs all of the codecs you need Plus the Firefox PlugIns for streaming media and the players needed for playing them and a whole lot of other things! It's a real winner!

Just one thing, there is a option for installing new graphics drivers. Like the saying goes, if it's not broken don't fix it! If you display works, UNTICK this option. Later when you are more comfortable with Ubuntu and the command line, then go messing around!

For WMV files get Mplayer and all the Mplayer addons for Firefox! Mplayer is brilliant when it comes to online content

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

Hope this helps,

Cheers,

Rudolf

---

