---
title: "Multimedia howto"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by anathema415 on 2008-02-02
Hi guys. Was using ubuntu a week or two ago. I had ti uninstall it. Now I've got it back.
There was a great howto guide for getting multimedia working properly on ubuntu (youtube, etc...) but now I can't find it. It was at least 12 pages long. I can't remember the author. I found it originally by searching 'youtube' but it seems to be gone:confused:

Is it still around or is there a comparable guide?

Thanks

---

### Post by A4006 on 2008-02-02
All you need for YouTube is the appropriate Firefox plugin.  Just visit the YouTube site, and when you go to watch a video it will have you install Adobe Flash Player.  Simple as that.

---

### Post by anathema415 on 2008-02-02
It was a lot more than youtube though. It dealt with restricted packages and codecs and various players, etc...

---

### Post by wolfen69 on 2008-02-02
if you are using gutsy, add this to terminal
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
and
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
for dvd playback
```
sudo apt-get install libdvdcss2 libdvdread
```
and
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by wolfen69 on 2008-02-02
for streaming media in firefox
```
sudo apt-get install mozilla-mplayer
```

flash may not work for you. if not, remove in synaptic, and install this file:
[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

---

### Post by Nhatz on 2008-02-02
try this......

for the flash player....

```
sudo apt-get install mozilla-plugin-gnash
```

for the other multimedia codecs....

```
sudo apt-get install ubuntu-restricted-extras
```

and... dont forget w32codecs

:guitar:

---

### Post by ubuntu-freak on 2008-02-02
Did you mean my [how-to](http://ubuntuforums.org/showthread.php?t=661833)? 
 
Nathan

---

### Post by anathema415 on 2008-02-02
> **reassuringlyoffensive said:**
> Did you mean my [how-to](http://ubuntuforums.org/showthread.php?t=661833)? 
 
Nathan

YES!!! Thank you Nathan! :KS

---

### Post by ubuntu-freak on 2008-02-02
> **anathema415 said:**
> YES!!! Thank you Nathan! :KS

 
Haha. Kinda funny. How could you not find it? Must have got buried a bit. I asked if it could be made a sticky. Not heard anything yet though.

---

### Post by anathema415 on 2008-02-02
> **reassuringlyoffensive said:**
> Haha. Kinda funny. How could you not find it? Must have got buried a bit. I asked if it could be made a sticky. Not heard anything yet though.

I dunno. I searched using a few keywords from both the title and the body, and went through the results each time. It wasn't there. It's bookmarked now though:)

---

