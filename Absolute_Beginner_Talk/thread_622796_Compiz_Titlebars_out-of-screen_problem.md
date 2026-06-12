---
title: "Compiz Titlebars out-of-screen problem"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by plopp37 on 2007-11-25
Hello,
I've installed compiz and it runs pretty good, but i have one problem since that -- as I open any window, its position starts just above my visible screen, so that the Titlebar is out of screen. I use top-position of the main panel, so the titlebar appears to be below that panel, but when I set the panel on the bottom of the screen, the windows still hide their titlebars out of sight. I always have to rightclick the window-tile on the panel and Move it somewhere on the screen and thats really annoying...
There is perhaps some simple solution, but as I am a newbie to ubuntu, I don't know it, can anybody help me, please?

Thanks alot

---

### Post by Ub1476 on 2007-11-25
Open CCSM (advanced desktop effects) and go down to Window management>Place windows>Placement mode>Choose what works best for you.

If you don't have advanced desktop effects installed, install it by typing this in the temrinal:

```
sudo apt-get install compizconfig-settings-manager
```

You can also install it through GUI in Synaptic if you would like.

---

### Post by DarkFienix on 2007-11-25
I had a similar issue and it turned out that I was using the wrong video (nVidia) drivers.  

Might be something to check too.

---

### Post by DutyDuty on 2007-11-25
You can also restart compiz to see if that fixes the problem. 
```
compiz --replace &
```

---

### Post by plopp37 on 2007-11-25
Well, it was that CCSM setting, I didnt have the Place Windows plugin ON, now it works well,
Thank you vm

---

