---
title: "PS3 able to see linux?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Distortedgamer on 2007-11-05
The PS3 is able to see videos, pictures, and music from any windows PC that is on the network. I am trying to find a way for it to see my Linux box. Does anyone know anything about this?

---

### Post by OoooMatron on 2007-11-05
Probalby have to share your folder in linux using SMB.

---

### Post by gmc on 2007-11-12
> **Distortedgamer said:**
> The PS3 is able to see videos, pictures, and music from any windows PC that is on the network. I am trying to find a way for it to see my Linux box. Does anyone know anything about this?

[URL="http://sourceforge.net/projects/ushare"]http://sourceforge.net/projects/ushare
[/URL]
This program works for me. I had to install libupnp-dev to compile it but once that was done, it was easy with the following command

**ushare -i eth0 -p 49152 -c /data/music *_-d_***

Fire up the PS3 and have is scan for an audio server. Should show up on the PS3 as ushare1.

Gord

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **OoooMatron said:**
> Probalby have to share your folder in linux using SMB.

this should work becuses it emulates a windows computer 
well atlest from the file sharing aspect of it ....... sort of but it should foul the ps3 :)

---

### Post by Distortedgamer on 2007-11-12
I ended up just getting MediaTomb 0.10.0. It has an option that allows it to share media with the PS3 specificly. Thanks for the advise.

---

