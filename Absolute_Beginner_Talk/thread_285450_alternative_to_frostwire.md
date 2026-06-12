---
title: "alternative to frostwire"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2006-10-26
ok well i got frostwire working but it really doesnt like to work that great, it tends to freeze alot and crash and stuff some guy (cant remember his name) said that it is because java is running in overdrive and he doesnt know how to fix that though

are there any other GOOD p2p programs out there that might work properly?

---

### Post by maaronB on 2006-10-26
frostwire is a bad imitation of limewire.  Limewire can be a little tricky to install (plenty of forum threads about it just do a search) but IMO is much more stable and useable.

---

### Post by Rackerz on 2006-10-26
Limewire is better than Frostwire.

---

### Post by rowster27 on 2006-10-26
try limewire for linux instead. :)

---

### Post by Fittersman on 2006-10-26
really, cuz in windows i actually liked frostwire better... well ill try imo and limewire any other suggestions are appreciated

---

### Post by blendmaster on 2006-10-26
Frostwire seems better to me, as it seems faster (and it's open-source).

Though, I guess problems occur with some programs on Linux, so trying LimeWire isn't such a bad idea.

---

### Post by blendmaster on 2006-10-26
> really, cuz in windows i actually liked frostwire better... well ill try imo and limewire any other suggestions are appreciated

Lol, I don't think IMO is software, it means In My Opinion in internet-lingo.

Don't feel bad though, I had to look up one of those abbreviations like a week ago.

---

### Post by Bloch on 2006-10-26
Nicotine is great for finding music. But the makers don't believe in documentation. It won't work "out of the box". You have to go to preferences and choose a dowmloads folder etc and then go back and click "connect"
(though why you would want to start Nicotine without trying to connect is not clear to me)

Pity the makers couldn't provide a "get started" wizard with it, it would have saved me 45 minutes of frustration.

---

### Post by th3t1nm4n on 2006-10-26
FrostWire runs fine for me, make sure that you have java installed properly.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_Gnutella_Client_.28FrostWire.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_Gnutella_Client_.28FrostWire.29)

If FrostWire fails to load, run it from a terminal to view the output, the problem will most likely be this: [http://ubuntuforums.org/showthread.php?p=1500733](http://ubuntuforums.org/showthread.php?p=1500733)

To fix it I just do ```
gksudo gedit /usr/bin/frostwire
```delete everything in there, paste ```
#!/bin/bash
cd /usr/lib/frostwire && bash runFrost.sh

```and save it.

This is why I prefer FrostWire to LimeWire: [http://frostwire.com/?module=about](http://frostwire.com/?module=about)

---

### Post by Fittersman on 2006-10-26
lol i was just googling for IMO

---

### Post by maaronB on 2006-10-26
> **Fittersman said:**
> lol i was just googling for IMO

Yeah, sorry I was just saying in my opinion limewire is more stable (stabler?).  there is no program called IMO.

---

### Post by seijuro on 2006-10-26
never had any problems with limewire on any linux distro I've tried it on just snag the "other os" version from their website unzip it and run the bin.

---

