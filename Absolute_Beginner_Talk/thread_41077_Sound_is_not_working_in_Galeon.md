---
title: "Sound is not working in Galeon"
date: 2005-06-11
forum: Absolute Beginner Talk
---

### Post by Kapre on 2005-06-11
Hi again!

Seems like I'm being hounded by one glitch at a time. Please bear with me coz I'm still a noob. 

I've installed Galeon and is using it now (seems great and is working well). But when I go and tested it on the website that I'me having a problem with Ffox, the sound is now gone. Please help.. :oops: 

Kapre

---

### Post by poofyhairguy on 2005-06-11
[QUOTE=Kapre]Hi again!

Seems like I'm being hounded by one glitch at a time. Please bear with me coz I'm still a noob. 

I've installed Galeon and is using it now (seems great and is working well). But when I go and tested it on the website that I'me having a problem with Ffox, the sound is now gone. Please help.. :oops: 

Kapre[/QUOTE]


As I said on the other thread, try Epiphany if your sound doesn't work in Galleon. Both are made by the same person, with epiphany being the newer project (its the official Gnome browser).

---

### Post by Kapre on 2005-06-11
Poofy,

I tried what you've said. I installed Ephipany and it also doesn't produce the sound that I have in Ffox. I removed Galeon and installed Ephipany but when I visited the sites (miniclip, edheads, etc..) it doesn't play sounds from those sites.

I'm switching now from Ephipany to Firefox (when sound is not produced on the other browser).

Kap

---

### Post by poofyhairguy on 2005-06-11
[QUOTE=Kapre]Poofy,

I tried what you've said. I installed Ephipany and it also doesn't produce the sound that I have in Ffox. I removed Galeon and installed Ephipany but when I visited the sites (miniclip, edheads, etc..) it doesn't play sounds from those sites.

I'm switching now from Ephipany to Firefox (when sound is not produced on the other browser).

Kap[/QUOTE]


Damn. Ok, last idea I have- use Mozilla. The real thing, not Firefox. It will work (it uses everything Firefox does) but won't suffer from the bug that got you in backports.

Sorry if it seems I'm giving you the run around. I'm trying to help, I promise.

---

### Post by TravisNewman on 2005-06-11
try running this in a terminal:

  sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

That's the fix for firefox not having sound, so it's quite possible it'll work in galeon

---

### Post by Kapre on 2005-06-12
Pooffy - thank you very much again. I know that you're trying help me and it is really a big help (for noobies like me). It just seems like when your new in linux your always having some glitch here and there and the best thing to do is consult with persons like you and also read the threads in the forum. Again, thank you very much.

Panicked - the sound is working on my Ffox but is not working in Ephipany, Galeon and it is working on Mozilla. I dont know why this is happening but is it because I'm using an internal sound card (CMI)??

Kapre

---

