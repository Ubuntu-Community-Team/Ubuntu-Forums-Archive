---
title: "What are good media players and C/C++ compilers for Linux?"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by Drezard on 2006-08-12
Hello. I have quite a few .asf, .avi and .wmv videos what is the best media in Linux to play those. The default one doesnt play them.

Also, What is a good C/C++ Compiler for Linux? 

Last one, What is a good HTML and PHP editor/s. One like Dreamweaver or Frontpage. 

Thank you, Daniel

---

### Post by jincast90 on 2006-08-12
> **Drezard said:**
> Hello. I have quite a few .asf, .avi and .wmv videos what is the best media in Linux to play those. The default one doesnt play them.
Thank you, Daniel

You need to downloade the codecs.

---

### Post by RudolfMDLT on 2006-08-12
Hi, this should help you sort out 99% of your Media troubles! Amarok is good for music. When playing movies and DVD's, i find Totem or Mplayer the bests, for asf and soforth, playinh them in FireFox would be best I think or mplayer. You also my want to use Xine as your steaming engine.

Quote:
Patent and licensing restrictions on media formats can complicate a free operating system's ability to distribute software that will support those formats.
- Quoted from the Ubuntu WIKI

Giving the wiki a read is always a good idea!:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

If you're new to Ubuntu, and you wish for a quick fix, this application is a solution to most of your media troubles! You would really do yourself some good by using Easy Ubuntu:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

It installs all of the codecs you need Plus the Firefox PlugIns for streaming media and the players needed for playing them and a whole lot of other things! It's a real winner!

Just one thing, there is a option for installing new graphics drivers. Like the saying goes, if it's not broken don't fix it! If you display works, UNTICK this option. Later when you are more comfortable with Ubuntu and the command line, then go messing around!

For WMV files get Mplayer and all the Mplayer addons for Firefox! Mplayer is brilliant when it comes to online content.

In synaptic do a search for mplayer and then for the mplayer FireFox plugins and install them ALL!

If you want to go it with the terminal(It is faster.):

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

PS: as for the IDEs end compilers I'm no programmer so can't help there, sorry! :)

---

### Post by Oppi on 2006-08-12
Hi

Like the others already posted: to get music, videos and DVD's working you have to install some codecs that aren't supported by Linux/Ubuntu by default due to legal rights concerns. 

But if you try 3rd Party Projects like

Automatix, BUMPS or Easyubuntu

everything will work fine.

I made it with BUMPS because it is the easiest and "smallest" way to make this issue work. 
Automatix and Easyubuntu are also great progs. but they give you lot more than just the multimedia codecs.

For a noob (like me) this programs are a great help :D 

greets, Oppi

---

