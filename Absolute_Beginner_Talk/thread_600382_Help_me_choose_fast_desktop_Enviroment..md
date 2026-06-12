---
title: "Help me choose fast desktop Enviroment."
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Gstyle on 2007-11-02
Which would be the best for my old and bit slow P3 machine?
Gnome and KDE are very slow on my machine.
I have p3 1.2 Ghz 256Ram, 40Hdd,  32 Video.
Xfce?
Fluxbox?
Or something else?
Good look for me is not important, i want make desktop run fast.

---

### Post by eidam655 on 2007-11-02
i'd guess that xfce offers a compromise between speed and lightness, fluxbox aims only on speed...

i think that xfce would be appropriate for your machine, but i'm not a pro ;)

---

### Post by philinux on 2007-11-02
i'm running Gutsy and it's fine on my old un.

---

### Post by RedSquirrel on 2007-11-02
For a desktop environment, Xfce would run pretty well on those specs. 

For something really light, fast, and extremely configurable, try a window manager. Fluxbox, Openbox, IceWm, etc. These can be made to look very nice with a little effort. ;) 

```
sudo apt-get install fluxbox && sudo update-menus
```

---

### Post by meborc on 2007-11-02
> **RedSquirrel said:**
> For a desktop environment, Xfce would run pretty well on those specs. 

For something really light, fast, and extremely configurable, try a window manager. Fluxbox, Openbox, IceWm, etc. These can be made to look very nice with a little effort. ;) 

```
sudo apt-get install fluxbox && sudo update-menus
```

i agree totally... i run fluxbox, and it is more beautiful than gnome will ever be (note: probably to my eyes only)... just look for some screenshots with fluxbox... it is beautiful and super-fast

i would suggest you try out [www.fluxbuntu.org](www.fluxbuntu.org) (only install cd available right now...)

---

### Post by Dr Small on 2007-11-02
> **Gstyle said:**
> Which would be the best for my old and bit slow P3 machine?
Gnome and KDE are very slow on my machine.
I have p3 1.2 Ghz 256Ram, 40Hdd,  32 Video.
Xfce?
Fluxbox?
Or something else?
Good look for me is not important, i want make desktop run fast.
Greetings,
You can check out a short list of different lightweight Window Mangers / Destkop Environments that I posted on my blog last night:
[http://php.8ez.com/drsmall/blog/?p=154](http://php.8ez.com/drsmall/blog/?p=154)

Dr Small

---

### Post by Niniel on 2007-11-02
If you can, put more RAM in that machine.
And/or try a lightweight distribution.

I have a PII/333 with 384 MB, and I can run Graf Puppy Linux with KDE (don't think it's the newest version though) at tolerable speeds, even with some transparency. It's by no means fast, but still ok. I'll probably switch to a different WM though to speed things up a bit.  Xubuntu, however, was extremely slow for me, although with your faster processor it may work for you.

---

### Post by vash5556 on 2007-11-02
XFCE or Fluxbox would probably be a couple good choice for you given your specs on your machine.

---

### Post by benton on 2007-11-03
I'm very, very happy running XFCE on a 1Ghz Pentium III laptop with 384MB of RAM and a slow 30GB HD. This is what I did:

1) Install a **command line system** only from the Gutsy ALTERNATE CD.
2) sudo aptitude install **xorg**
3) sudo aptitude install **xfce4**

Then I added:

sudo aptitude install **nvidia-glx** (nvidia restricted driver for the nvidia card on my laptop)
sudo aptitude install **vlc** (will play any multimedia file you throw at it, no extra codecs to install)
sudo aptitude remove **xfmedia** (thanks to vlc I don't need it)

Search the forums for suggestions on lightweight apps for internet browsing, email, etc.

I can tell you the laptop is very responsive and it feels as powerful as a today's laptop running Vista (or the full Ubuntu 7.10 install from the live CD for that matter :) )

I'm happy with no login manager, as speed and resources are more important to me. The machine is very responsive and as a multimedia machine it runs great. 

XFCE Rocks!

---

