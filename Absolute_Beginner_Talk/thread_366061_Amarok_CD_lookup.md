---
title: "Amarok CD lookup"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by noisc on 2007-02-20
I'm trying to get the feel of Amarok on Edgy, and, much to my chagrin, I can't figure out how to make Amarok access a CDDB for CD information.

Basically, I pop in a CD, I can play it, but Amarok won't lookup CD information automatically, and I can't find out how to force it to do so. The tracks and artist all have default 'track 3', 'album artist' names. Honestly, I've only tried one CD, but it's hardly an obscure one, and I *know* that freedb has it. (Ironically, I've found out how to look up album art on Amazon from Amarok, but that's really just icing for a cake that I have yet to bake.)

I'm using Amarok 1.4.3. Under Settings->Configure Amarok->Engine, my CDDB server is set to freedb.freedb.org.

Anybody know how to lookup CD info in Amarok?

---

### Post by grahams on 2007-02-26
If your Internet connection is via a proxy server, I think you may have run into the same issue I did. Amarok is written for KDE it doesn't pick up the Gnome network settings and therefore can't use CDDB or download album art. I switched the Exaile ([www.exaile.org)](www.exaile.org)), which is written for Gnome, so it starts faster (no KDE libraries to load), has many Amarok like features and is evolving quickly. 

I'm using 0.2.8 on edgy from this install [http://www.exaile.org/files/exaile_0.2.8_i386.deb](http://www.exaile.org/files/exaile_0.2.8_i386.deb)

---

