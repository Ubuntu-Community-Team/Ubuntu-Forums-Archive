---
title: "AMD64 Questions"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Icemanyurt on 2007-01-07
Just some basic questions about installing onto a machine running an Athlon 64 2800+.

I did a forum search about this, but I could not come up with anything definitive, only rumor and whisper.

What are the issues people run into and how hard are they to overcome? 
Does the standard version work better overall?

Any links, resources or advice would be great.  
Thanks

---

### Post by jem7v on 2007-01-07
I've installed both the AMD64 and the i386 versions on the same processor you have, and they both worked fine.  It's sometimes easier to find drivers and programs for the i386 version because a lot of third-party companies don't release .debs for 64 bit architectures.  I always hear that the 64 bit version makes better use of the processing power, but I didn't notice any performance difference in typical usage.

---

### Post by Tux Aubrey on 2007-01-07
I recently set up a machine for my son running an AMD 64 processor but decided to go with the standard (6.10) 32 bit Ubuntu after reading of people's problems with the 64 bit version (mainly to do with lack of true 64 bit packages and unsupported extensions in Firefox, I think).

I did have a few problems with his ASROCK SATA motherboard (very slow boot times) but this was fixed with the latest kernel update.

Other than that, there were no issues at all with the installation and once all the non-free codecs were installed (via Automatix) he was as happy as pig in mud.

---

### Post by sloggerkhan on 2007-01-07
I had both 64 bit and 32 bit on my comp under Dapper. I think I got SLIGHTLY better battery life out of 64 bit, but didn't notice much of a performance difference. That said, video codecs and flash were a much bigger issue on 64 bit (at least at the time.) and I didn't want to deal with it (chroot) because I was pretty much a noob, so I use 32 bit now. I might do a 64 bit install sometime, but no reason to right now.

---

### Post by Icemanyurt on 2007-01-07
ok, really dumb question: What is automatix?

I have used the synaptic package manager, add/remove manager and system updater, is it one of those?

---

### Post by Tux Aubrey on 2007-01-07
Ahh!  Automatix is a third-party installer wizard that grabs codecs and other third-party stuff for you.  It's a pretty simple install process from [www.getautomatix.com](www.getautomatix.com)

---

### Post by sloggerkhan on 2007-01-10
automatix used to be really nice back before win32 codecs and browser plugins showed up in the add/remove menu.

---

