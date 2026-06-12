---
title: "[SOLVED] Little Flash Videos from YouTube or other Video Sites &amp;quot;How to View?&amp;quot;"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-18
On my Laptop:

Looking in to "File System > tmp" folder I noticed the flash videos were showing up there when I was viewing them in Firefox, and continue to show up in the "tmp" folder as long as I had firefox open.

the flash movies show up nice with a movie icon (with each movies current picture) and when I double click it plays great in "Totem Movie Player 2.18.1"

This is great, as such I just drag and drop the flash videos from "tmp" to my home folder

cool, saves me some firefox plugins
--------------------------------------------
--------------------------------------------

On my uncles PC:

(so I just installed Feisty on my uncles PC, and I'm trying to avoid putting Automatix there)

anyway, I followed all the instructions from ubuntuforums and got all the stuff I need installed (Mediaubuntu, Restricted... etc)

the same "Totem Movie Player 2.18.1" is here and the flash and youtube movies all play in firefox, but when I look in to his "tmp" folder the flash movies are there but they look like ordinary text files and when I drag and drop them in the home folder and wanna play them, it doesn't work.

(In windows I use the flv-player)

please any help, thanks

---

### Post by RevThwack on 2007-09-18
Use synaptic package manager to install gnash or flashplugin-nonfree. After that, movie player should be able to play them just fine.

---

### Post by MozartlovesUbun2 on 2007-09-18
> **RevThwack said:**
> Use synaptic package manager to install gnash or flashplugin-nonfree. After that, movie player should be able to play them just fine.

Sorry, that didn't help :(

the video files still show up as plain white files and don't open

---

### Post by RevThwack on 2007-09-18
Since I'm not sure what all packages you have installed, here are the ones I've got surrounding flash.

flashplugin-nonfree
libflash0c2
libflash-swfplayer
libswfdec0.3

If that doesn't work, run a search for "flash" in synaptic and post which packages it shows you having installed.

---

### Post by MozartlovesUbun2 on 2007-09-18
> **RevThwack said:**
> Since I'm not sure what all packages you have installed, here are the ones I've got surrounding flash.

flashplugin-nonfree
libflash0c2
libflash-swfplayer
libswfdec0.3

If that doesn't work, run a search for "flash" in synaptic and post which packages it shows you having installed.

ok the middle two were missing

libflash0c2
libflash-swfplayer

installed them but still no luck :(

upon right-clicking it does correctly say "open with Movie Player"

after I take the file out from "tmp" I can't view them, can you?

as mentioned above I can view them in my laptop

so what could be missing that it doesn't do the same on the home PC?

---

