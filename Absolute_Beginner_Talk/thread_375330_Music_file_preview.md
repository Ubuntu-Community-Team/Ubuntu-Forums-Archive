---
title: "Music file preview"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Resurrection on 2007-03-03
This is more a less a thread just to let others know of a cool feature I found, which is why I put it here in Absolute beginners as the best place.

I had no idea that if you hover over an .mp3 file in Gnome (Nautilus) that it would start playing it for you, without launching a player, sort of like previewing a thumbnail of a picture.  Very cool.  Been using Ubuntu for 1.5 years and never noticed this before.

Is this a feature of Nautilus, Ubuntu, or something else?  Whoever implemented it, thank you!

---

### Post by Perfect Storm on 2007-03-03
Well, on my system it's not installed by default. Thelibs are called: mpg123

---

### Post by Resurrection on 2007-03-03
I don't remember installing, that but sure enough, I have it installed.  I wonder what installed it?  Does Beep, VLC or some other player depend on it?

Actually the lib is mpg321 (related to mpg123).

---

### Post by Perfect Storm on 2007-03-03
I checked both of their dependency list and it's not list.

---

### Post by Resurrection on 2007-03-03
Hmm, oddly enough, I searched my history in Synaptic and it can't find when that package was installed.  I thought if I could find that I might be able to find out what installed it.  I didn't install it on my own.  Any way to check what depends that package?  Isn't that reverse dependency?

Edit:  

Did this in terminal:

> sudo apt-cache showpkg mpg321
and got:

> Package: mpg321
Versions: 
0.2.10.3 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages
                  MD5: 5a8d8aac1d2eb9cc6a4d1f0ebcf7b934


Reverse Depends: 
  ubuntu-seveas,mpg321
  vux,mpg321
  terminatorx,mpg321
  ripperx,mpg321
  randomplay,mpg321
  pytone,mpg321
  playmp3list,mpg321
  orpheus,mpg321
  normalize-audio,mpg321
  music123,mpg321
  mserv,mpg321
  mpg123-el,mpg321
  mp3roaster,mpg321
  mp3check,mpg321
  mp3burn,mpg321 0.1.5.2
  mp32ogg,mpg321 0.2
  moosic,mpg321
  juke,mpg321
  irmp3,mpg321
  gqmpeg,mpg321
  gjay,mpg321
  eroaster,mpg321
  emms,mpg321
  ecasound,mpg321
  cwcdr,mpg321
  cplay,mpg321
  claw4,mpg321
  cdrbq,mpg321
  burn,mpg321 0.2.10.3
  arson,mpg321
  advi-examples,mpg321
Dependencies: 
0.2.10.3 - libao2 (2 0.8.5) libc6 (2 2.3.2.ds1-4) libid3tag0 (2 0.15.0b) libmad0 (2 0.15.1b) zlib1g (2 1:1.2.1) 
Provides: 
0.2.10.3 - mp3-decoder mpg123 
Reverse Provides: 


---

### Post by Perfect Storm on 2007-03-03
Must be dependency of dependency of dependecy :P

---

### Post by mcduck on 2007-03-03
> **Resurrection said:**
> I don't remember installing, that but sure enough, I have it installed.  I wonder what installed it?  Does Beep, VLC or some other player depend on it?

Actually the lib is mpg321 (related to mpg123).

mpg123 and mpg321 are separate packages, both work.

Also get the 'vorbis-tools'-package to enable preview for Ogg. I still haven't found out what package is needed for Flac.

---

### Post by SigmundFreud on 2007-03-03
Is there any way to get the same thing with Kubuntu (KDE)?

---

### Post by rolando2424 on 2007-03-03
I've found about that feature a few months ago :D

---

### Post by Resurrection on 2007-03-04
> **rolando2424 said:**
> I've found about that feature a few months ago :D

Dude why didn't you let me know?:) 

Next time tell everyone!:guitar:

---

### Post by dommyOZ on 2007-04-29
> **mcduck said:**
> mpg123 and mpg321 are separate packages, both work.

Also get the 'vorbis-tools'-package to enable preview for Ogg. I still haven't found out what package is needed for Flac.

Did you happen to find a way to preview flac files??

---

