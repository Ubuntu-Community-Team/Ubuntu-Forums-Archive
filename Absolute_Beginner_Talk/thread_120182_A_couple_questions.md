---
title: "A couple questions"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Riiktar on 2006-01-21
Okay, my friend just sold me on dropping windows XP to transfer over to Ubuntu.  This guy has always used linux, but fixes a school districts windows so I trust him.  I did it and I love it.  Never even used the internet on a linux comp.  Easy transfer if you look and follow some directions.  Anyways now I need some more learning,

I found a driver for my conextant/riptide modem/soundcard BUT only for the modem.  Is there a riptide driver for ubuntu?  I would really like some sound!!

Question 2

I want to stream videos off teh internet such as items from say.....Ebaumsworld videos.  Normaly I would use winamp BUT obviously not now.  When I try to stream, Totem comes up and says my codecs are all wrong.  How can I eaither istall the codecs OR just find an install of a complete working package out of the box.  

Thank you for any help.  3 days of Ubuntu now and I LOVE IT@!!

---

### Post by stuporglue on 2006-01-21
Q2. 

You need to enable "multiverse" repositories in Synaptic, or in your sources.list. Search the forums for "multiverse" and you'll find a tutorial. After that, from the command line run "sudo apt-get install gstreamer0.8*" and all sorts of fun codecs will be installed for you. Possibly/Probably the ones you're looking for too. I haven't ever checked out ebaumsworld.

---

### Post by diggs on 2006-01-21
Also, stickied in this forum is a thread about automatix. install that, it will allow you to install all your codecs, file players and a lot of other things very easily. couple of mouseclicks, go take a dump and all the programs are installed and ready to go!

---

### Post by Riiktar on 2006-01-21
Thanks you for all your help.  I did find the automatix while searching for multiverse help lol.  Now I just need to figure out my damn sound card.  THanks again.

---

### Post by az on 2006-01-21
No dice on the soundcard.  Conexant only made proprietairy drivers for it and never bothered to update them for the 2.6 kernel.  That is a disadvantage of closed-source drivers.  Had they released them as FLOSS, they would have been updated for free by now.

Blame the manufacturer.

---

### Post by Riiktar on 2006-01-21
[QUOTE=azz]No dice on the soundcard.  Conexant only made proprietairy drivers for it and never bothered to update them for the 2.6 kernel.  That is a disadvantage of closed-source drivers.  Had they released them as FLOSS, they would have been updated for free by now.

Blame the manufacturer.[/QUOTE]

Eh it's a peice of shit sound card anyways.  I fixed up a 98 HP and the motherboard, P3 processor and the sound card I left in.  I think I may have a SB 16 around here somewhere.  I just wanna hear videos dammit.  My SB live went in my XP music computer.  If anyone knows how to get ableton 5 working in linux, ill switch the cards.

---

