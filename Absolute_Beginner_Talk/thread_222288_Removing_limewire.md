---
title: "Removing limewire"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by GuitarHero on 2006-07-24
I installed a limewire rpm with alien but the install doesnt seem to work.  I try to open it and nothing happens.  Its in the menu but its not in synaptic.  I was trying to get rid of it but i cant figure out how without it being in synaptic or sudo alien/apt-get remove limewire not working.

---

### Post by trivialpackets on 2006-07-24
I'm not sure.  I always recall being able to see programs I installed using alien.  I'll look when I get home at somethign I installed with alien.  With Limewire, you are much better off using the bin file that they have, or an even better alternative is FrostWire, which is an opensourced version of limewire.  You can get that using automatix, but I'm not sure of the repo needed for it without.

Also, just something I usually try when I can't get something like that to work.  Try to run it from the terminal.  Usually, it means I'm missing something I need.  (Your system has JAVA?).  Running limewire from the terminal from wherever it is located should give you more information as to why it is not running for you.  Just a tip.

---

### Post by agurk on 2006-07-24
Another alternative Gnutella klient (and a personal favourite of mine) is [Phex](http://phex.kouk.de/mambo), very helpful and friendly spirit in their forums as well.

---

### Post by whitegorilla on 2006-07-25
I installed limewire for the first time last night and I had to install certain java files as well for limewire to work.  I already had some form of java installed, so I was a bit confused at first.

---

### Post by aeto on 2006-07-25
frostwire is kind of limited. but does the work..

---

### Post by GuitarHero on 2006-07-27
Yes. I have java installed.  Now I'm just looking to remove it.  How can I do this?  apt-get, aptitude, alien, and synaptic, tried em all.

---

### Post by arnieboy on 2006-07-27
> **GuitarHero said:**
> I installed a limewire rpm with alien but the install doesnt seem to work.  I try to open it and nothing happens.  Its in the menu but its not in synaptic.  I was trying to get rid of it but i cant figure out how without it being in synaptic or sudo alien/apt-get remove limewire not working.

u probably only have the menu item installed (nothing else). do a search for limewire.desktop (or something similar though it has to be a .desktop file) in /usr/share/applications/ and remove it as sudo.

---

