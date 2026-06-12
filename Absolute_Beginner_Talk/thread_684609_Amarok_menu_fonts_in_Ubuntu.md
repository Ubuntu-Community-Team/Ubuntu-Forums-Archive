---
title: "Amarok menu fonts in Ubuntu"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by inverseroom on 2008-02-01
I'm using Amarok,and like it, but I can't use the appearance settings to change the menu font.  I'm not using text smoothing of any kind, and the stock font looks rather dreadful.  I realize people running KDE have more options here, but can I adjust this in gnome?  The Amarok forum seems to be a bit anti-gnome and I couldn't find any useful anwers there.  Thanks!

---

### Post by airbornemist6 on 2008-02-01
I believe you can change themes in amarok, this is an old thread, very old, but it might be worth a look:
[http://ubuntuforums.org/showthread.php?t=105859](http://ubuntuforums.org/showthread.php?t=105859)

---

### Post by justsomedude on 2008-02-01
You can install KDE's control panel and adjust all font settings (including antialiasing) for KDE applications there:

```
sudo apt-get install kcontrol
```

This works for amarok, I do it that way. But be careful, this will install quite a large bunch of KDE libraries...

---

### Post by inverseroom on 2008-02-01
Thanks!  I did see that thread...(yes, a noob who searches!)...but I still would like to change that specific font to one that I prefer.  The themes I found seem to have the same menu font.

My non-smoothing habits make Tahoma the screen font of choice...I've already changed the other fonts in Amarok to Tahoma but that one isn't accessible.

---

### Post by inverseroom on 2008-02-01
> **justsomedude said:**
> You can install KDE's control panel and adjust all font settings (including antialiasing) for KDE applications there:

```
sudo apt-get install kcontrol
```

This works for amarok, I do it that way. But be careful, this will install quite a large bunch of KDE libraries...

Ah, I saw that answer somewhere, but I didn't realize it would be useful in GNOME.  Can i just uncheck the libraries in question and install only the app?

---

### Post by airbornemist6 on 2008-02-01
> **justsomedude said:**
> You can install KDE's control panel and adjust all font settings (including antialiasing) for KDE applications there:

```
sudo apt-get install kcontrol
```

This works for amarok, I do it that way. But be careful, this will install quite a large bunch of KDE libraries...
Yes, but installing things doesn't generally break things on linux, as unlike on windows, most packages just go unused unless you actually need them.

> **inverseroom said:**
> Thanks!  I did see that thread...(yes, a noob who searches!)...but I still would like to change that specific font to one that I prefer.  The themes I found seem to have the same menu font.

My non-smoothing habits make Tahoma the screen font of choice...I've already changed the other fonts in Amarok to Tahoma but that one isn't accessible.
Proud to hear I wasn't the only noob that used search. Congrats I present you with a cookie. But, I would suggest you go ahead and try what justsomedude said. I had forgotten about installing kcontrol. Sometimes a lot of the better applications are KDE, and you pretty much HAVE TO have kcontrol to make them readable.

EDIT:
No, you cannot uninstall dependencies. When you install something, it will only install what is necessary, and there is really no need to uncheck them anyway because having KDE running on a gnome desktop isn't going to hurt anything.

---

### Post by inverseroom on 2008-02-01
Got it, thanks again!

I honestly can't believe how quickly questions get answered around here.  This community is amazing.

---

### Post by justsomedude on 2008-02-01
> Ah, I saw that answer somewhere, but I didn't realize it would be useful in GNOME. Can i just uncheck the libraries in question and install only the app?

No, you will have to install all the dependencies.

EDIT:

> I honestly can't believe how quickly questions get answered around here. This community is amazing.

Me too. ;) And airbornemist6 is right, this will not break stuff. I just meant it would be a rather large download...

---

