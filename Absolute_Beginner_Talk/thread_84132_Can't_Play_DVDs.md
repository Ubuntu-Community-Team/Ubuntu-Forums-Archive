---
title: "Can't Play DVDs"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by asombill on 2005-10-30
Yep, another newbie to Linux. Got most of the things working, well for the 1 day I have had Breezy installed. But I can not seem DVDs to play. I open Totem and try to play a DVD and get:

Totem could not play 'dvd://'.

Could not read title information for DVD.


Help? 
Thanks in advance, you guys are awesome!

---

### Post by Xian on 2005-10-30
Please read the wiki entry [Playing Movies & Music](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies).

---

### Post by asombill on 2005-10-30
[QUOTE=Xian]Please read the wiki entry [Playing Movies & Music](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies).[/QUOTE]

Following instructions,  I get this:
/usr/share/doc/libdvdread3/examples/install-css.sh: line 39: dpkg-source: command not found

---

### Post by Donnut on 2005-10-30
Also, use Ogle.  You can find it in Add Aplications or Synaptic.

---

### Post by goodmanbrown on 2005-10-31
If your hardware is properly configured there are only two things you should have to do to play DVDs.  First:

```
sudo apt-get install totem-xine
```

This will remove totem-gstreamer, which can't yet play DVDs, and install totem-xine instead.  Second:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

That will install the decryption software needed to watch DVDs.  If you should happen to get a "command not found" error when you run the above command, you might need first to run:

```
sudo apt-get install libdvdread3
```

---

### Post by goodmanbrown on 2005-10-31
Whoops-- sorry.  Didn't read your follow-up post carefully enough.

I'm not sure why dpkg-source isn't installed on your system by default, but to get it, just:

```
sudo apt-get install dpkg-dev
```

---

