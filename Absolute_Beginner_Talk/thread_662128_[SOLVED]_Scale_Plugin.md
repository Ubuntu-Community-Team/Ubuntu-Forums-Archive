---
title: "[SOLVED] Scale Plugin"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Valthinos on 2008-01-08
I was searching around google for an expose-like feature for Ubuntu. Someone recommended the scale plugin. How do I get this program please as I'd really like to try it out.

Really appreciate all the help.

---

### Post by Pevichaey5 on 2008-01-08
you will need full 3d support on your graphics card and scale is just a plugin for the compiz window manager

i haven't achieved xgl on ubuntu yet but thats what you need

---

### Post by Valthinos on 2008-01-08
I'm pretty sure I have 3d support and I'm using compiz.

---

### Post by Pevichaey5 on 2008-01-08
its on this site
[http://wiki.compiz-fusion.org/Plugins/Scale](http://wiki.compiz-fusion.org/Plugins/Scale)

---

### Post by aCiD2 on 2008-01-08
Hi Valthinos, which Ubuntu are you running? Gutsy Gibbon comes with Compiz support, providing you have sufficient drivers. To activate it go to Preferences Menu, Appearence then choose Visual Effects. Choose "Extra."

Next, you should probably install compiz-settings-manager, as this is a nice front end to configuring compiz. Just do:

```
sudo apt-get install compiz-settings-manager
```

This should add a "Advanced Desktop Effects Settings" applet. If you fire this up, you can enable Scale and change settings.

Hope this helps :)

---

### Post by annda on 2008-01-08
you need to enable full desktop effects in system>preferences>appearance and also install a configuration tool for compiz (this is what runs all the effects)
```

sudo apt-get install compizconfig-settings-manager
```

then you will be able to configure how you want to launch/initiate the scale plugin in system>preferences>advanced desktop effects settings

---

### Post by Valthinos on 2008-01-08
W00T! It works! Thanks! Do you know how I could activate it with the 4th button on my mouse though?

---

