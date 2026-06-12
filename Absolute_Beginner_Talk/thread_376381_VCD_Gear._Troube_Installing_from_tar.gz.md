---
title: "VCD Gear. Troube Installing from tar.gz"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by adarkmethod on 2007-03-04
I recently downloaded a couple versions of VCD so i can use my .bin/cue movies, but i cant get it to compile and isntall.

vcdgear176-040415_linux.tar.gz is one of the files.

edit: sorry for being such a n00b. Forgive me, for i have been stuck on Windoze for 10 years, its a lot to unlearn

---

### Post by taurus on 2007-03-04
Do you want to watch .bin movie?  Try mplayer.

```
gmplayer **filename.bin**
```

[https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

And if you want to know how to install something in Ubuntu, then read these two guides.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by adarkmethod on 2007-03-04
i actually prefer VLC Player, but im actually trying to burn a movie i ripped back to DVD, my original copy is pretty scratched up, so i need to be able to load it into VCD gear, so i can convert it to MPG, and then i beleive most burners can convert the .mpg to .Vob which is compatible with DVD players

---

### Post by taurus on 2007-03-04
Why go to all the trouble.  K3b can burn cue/bin directly.

```
sudo aptitude update
sudo aptitude install k3b
```

---

### Post by adarkmethod on 2007-03-04
awesome, im going for that now, thanx.

---

### Post by adarkmethod on 2007-03-04
well, i got K3bInstalled and running, but when i tried to nurm, it jsut burned a pure data disk, which won't play in my DVD player, i looked at their site and searched around a bit, and i cant seem to find anyone with working isntructions for how to burn a .bin/cue to a playable DVD movie

---

### Post by adarkmethod on 2007-03-05
ok, i tried both Nero and K3B but noth only burned Data disks instead of wathable DVDs. I also have an older version of VCD Gear now installed, but i cant get it to start to save my live

---

