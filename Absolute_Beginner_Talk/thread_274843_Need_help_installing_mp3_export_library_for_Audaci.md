---
title: "Need help installing mp3 export library for Audacity"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-10
Hey everyone,
     I'm having some difficulty installing liblame0 for *Audacity *to use in converting m4as and such to mp3s. The problem is that *Synaptic *swears on a stack of bibles sprinkled with god's own weewee that liblame is already installed, but that's simply not true. I've toyed with the idea of uninstalling and reinstalling, but it looks like I'll have to uninstall a slew of related apps, which I'd like to avoid. Has anyone had similar problems? Does anyone have recommendations?
     By the way, I've downloaded the library from *Sourceforge*, and leaving aside the problem that I don't know how to bypass simple security measures on Dapper so I can copy and paste the pertinent files into the pertinent folders, there is, firstly, the question of whether this is even a good idea, and secondly the fact that the file which *Audacity *is looking for - namely libmp3lame.so - is not present anywhere in the download. All of the folders have the right names, but the file is awol. Curiouser and curiouser. TIA.

---

### Post by GarethMB on 2006-10-10
Please check in usr/lib for libmp3lame.so

If it's not there, i'll see what i can do.

---

### Post by ricardisimo on 2006-10-10
> **GarethMB said:**
> Please check in usr/lib for libmp3lame.so

If it's not there, i'll see what i can do.

Never mind. There was a little check box I had to untick, which only allowed it to look for exactly "libmp3lame.so" and not "libmp3lame.so.0.0.0", which is another option (albeit an odd one). Sorry for the stupidity everyone, and thanks.

---

### Post by doobit on 2006-10-10
> **ricardisimo said:**
> Never mind. There was a little check box I had to untick, which only allowed it to look for exactly "libmp3lame.so" and not "libmp3lame.so.0.0.0", which is another option (albeit an odd one). Sorry for the stupidity everyone, and thanks.

libmp3lame.so.0.0.0 is the extended library, which is actually the one I had to choose on my system to get it to work.

---

