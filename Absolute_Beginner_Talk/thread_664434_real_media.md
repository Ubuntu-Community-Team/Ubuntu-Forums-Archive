---
title: "real media"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by karthikophobia on 2008-01-11
Hi
Can anyone tell me how to play rm/rmvb files in gutsy
I tried suggestions from many links but they didn.t work:(

thanq

---

### Post by peabody on 2008-01-11
If you have the w32codecs package installed from Mediabuntu, real media seems to play well for me using the 'mplayer' media player.

And of course, observe all legal disclaimers.

---

### Post by aktiwers on 2008-01-11
```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
``````

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

When done.. click this link to install RealPlayer:
[apt:realplayer](apt:realplayer) 

Then open the files with Realplayer or set it to default by right-clicking the file, pick properties, pick the "open With" tab and pick realplayer.

---

### Post by AndyCooll on 2008-01-11
> **aktiwers said:**
> ```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
``````

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

You actually have a choice once you've added the Medibuntu repos as the first two lines above explain. It isn't necessary to install RealPlayer, though you could if you so wish. However as indicated in an earlier post alternatively you could just install the w32codecs. You can then play rm files in your preferred media player (MPlayer, Totem etc).

:cool:

---

### Post by bhavi on 2008-01-11
yes..but in totem the sound is really dodgy... :lolflag:

---

### Post by karthikophobia on 2008-01-12
thanx for ur help got it to work

---

