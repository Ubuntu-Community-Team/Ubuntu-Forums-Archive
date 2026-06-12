---
title: "I have Automatix now but midi files don't work."
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-11-30
I have Automatix now but midi files don't work.  Is there some certain checkbox that deals with midi codecs.  If so what do I need to do?
If not how can I listen to midi files on Linux?

---

### Post by xyz on 2006-11-30
Hi,
I've had some luck with:
[playmidi]("http://www.die.net/doc/linux/man/man1/playmidi.1.html")
```
sudo aptitude install playmidi
```
Also in Synaptic!
> MIDI player
Playmidi is a MIDI file player that will play back using FM, GUS,
SoundBlaster or external MIDI.  It also supports Creative Music
Files (CMF) and Microsoft RIFF (RMI) files and large MIDI archives
from games such as Ultima 7.

There are two interfaces: text and X.
Good luck!
Also [http://linux-sound.org/midi.html](http://linux-sound.org/midi.html) Midi Software

---

### Post by jingo811 on 2006-11-30
how do I properly uninstall playmidi?  I don't like having to type in each and every midi file name I want to listen to.  I prefer plain-dumb-click-and-listen GUI players.

---

### Post by TheRingmaster on 2006-11-30
sudo aptitude remove playmidi

---

### Post by jingo811 on 2006-11-30
OK after uninstalling it the aptitude way I didn't know what else to do other than re-installing the same program again this time through Synaptic.

How do I access the X part of playmidi.  (which I assume is the graphical version of this program?)

---

### Post by TheRingmaster on 2006-11-30
you can play midi files with xmms if you have the xmms-midi plugin. I would recommend this more than playmidi.

(all available in synaptic)

---

### Post by jingo811 on 2006-11-30
Sorry to bother you again but I can't find xmms-midi in Synaptic.  It finds nothing when I search "xmms midi" or "xmms-midi" only when I search xmms do I get a bunch of weird programs that's not even part of the xmms.

What am I doing wrong?

---

### Post by compmodder26 on 2006-11-30
It should be in the universe repositories.

---

### Post by jingo811 on 2006-11-30
OK I think I will need more hands-on 1,2,3 kind of instructions!  I'm still newbie to repository stuff.  I followed this guide and replaced the whole content with this:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)
> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

I see universe here and there but it doesn't tell me much.  What else do I need to do from here?

---

### Post by viciouslime on 2006-11-30
My method is to install timidity and timidity-interfaces-extra, then right click your midi file, select open with other application then in the open with other command box (click the arrow to get it) enter timidity -ig.

From now on just double click your midi files and voila :D

EDIT Let me know if you get stuck! I'll try my best to help you

---

### Post by jingo811 on 2006-11-30
It finally worked but it's a very slow process when you want to select several midi files to listen to.  And you can't intuitively delete files and manage them :( 

Is there really no as-good-as-Winamp alternative for Linux that can handle mp3 and midi files out there?

---

