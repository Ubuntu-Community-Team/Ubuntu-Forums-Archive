---
title: "[SOLVED] vlc dvd problems - newbie"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by dave00001 on 2007-12-15
I've just installed gutsy 7.10, and downloaded VLC media player.  The problem is, I can't get VLC to play any DVDs - when I insert a disc or try to open the dvd from VLC, nothing happens. 
Totem can play some DVDs, but not others, because of uninstalled plugins.  I really want to use VLC for all my dvds/avis/mpeg... has anybody had the same problems??

---

### Post by Pumalite on 2007-12-15
You have to get a few codecs. Add Medibuntu to your sources.list. Also:
sudo apt-get install ubuntu-restricted-extras
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by shirilover on 2007-12-15
You might need to install libdvdcss2 to play back commercial DVDs.
Installing any other codecs will have no effect on VLC's video playing since it uses its own.

---

### Post by JillSwift on 2007-12-15
For me, VLC was initially pointed at a non-existent device and I had to manually change it to get it to play DVDs.

---

### Post by dave00001 on 2007-12-15
How would I add Medibuntu to my sources.list?  I've looked at the documentation and it doesn't look very straightforward.... Nor does it look like there are any codecs for VLC in there.  --Also, I can't seem to find my device paths to configure VLC...

---

### Post by LaRoza on 2007-12-15
> **dave00001 said:**
> How would I add Medibuntu to my sources.list?  I've looked at the documentation and it doesn't look very straightforward.... Nor does it look like there are any codecs for VLC in there.  --Also, I can't seem to find my device paths to configure VLC...

It is very straightforward, in Gutsy:

```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

Then:

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

---

### Post by ericartman on 2007-12-15
Check out

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

always worked for me

Cart

---

### Post by Pumalite on 2007-12-15
Read my links carefully. It's very clear. You can install all the codecs you need after that. Take your time. There is a learning curve and it requires patience.

---

### Post by dave00001 on 2007-12-15
Ok, I've added Medibuntu, and now I can play certain DVD's in VLC.  One problem - some dvds start to play, but stop for some reason.  I'm wondering if this is a DVD region thing or if there are any more packages I need to install.  Maybe Mplayer is a better choice...

---

### Post by DrMilo on 2007-12-16
I have found that you need at least Totem and VLC to play nearly all the formats, even then some will give you problems.

---

### Post by stchman on 2007-12-16
> **dave00001 said:**
> I've just installed gutsy 7.10, and downloaded VLC media player.  The problem is, I can't get VLC to play any DVDs - when I insert a disc or try to open the dvd from VLC, nothing happens. 
Totem can play some DVDs, but not others, because of uninstalled plugins.  I really want to use VLC for all my dvds/avis/mpeg... has anybody had the same problems??

I have a tutorial for playing encrypted DVDs.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by dave00001 on 2007-12-17
Thanks for your help with Medibuntu.  VLC works perfectly now for most dvds (but still can't open some).

---

### Post by philinux on 2007-12-17
Install and run

regionset 

from  synaptic

dont change the region unless you have too

---

### Post by dave00001 on 2007-12-18
Works like a charm now...  Thanks to all who helped out!!

---

