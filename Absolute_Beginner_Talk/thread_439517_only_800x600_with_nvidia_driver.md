---
title: "only 800x600 with nvidia driver"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by toddr on 2007-05-10
Greetings
I just did a fresh install of Fiesty and it looks great! The only problem is after installing the nvidia drivers I could only achieve 800x600 resolution. Before I installed the drivers, I had 1024x768. I don't know if it matters, but I installed them via Automatix2. Any help would be appreciated. thanks for looking

---

### Post by annda on 2007-05-10
try nvidia settings. if you can't find it in the menus, go to good old terminal:
```

gksu nvidia-settings
```

remember to save the X configuration file before restarting X / rebooting.

p.s. it's a good idea to back up /etc/X11/xorg.conf first.

---

### Post by stmiller on 2007-05-10
The 'official' ubuntu Feisty way is to install these things:

In a terminal:

sudo apt-get install linux-restricted-modules nvidia-glx-new nvidia-settings

Then reboot and it will work.

---

### Post by LollYouSuckZor on 2007-05-10
^^ Dont complain, I [had] 640 x 400.

---

### Post by toddr on 2007-05-11
I don't know if it matters, but the nvidia card is an old 32mb tnt2. Should I still install the new drivers?

---

### Post by heimo on 2007-05-11
> **toddr said:**
> I don't know if it matters, but the nvidia card is an old 32mb tnt2. Should I still install the new drivers?

I'd try nv driver.

---

### Post by toddr on 2007-05-11
Hey it works now! This doesn't make sense, but I uninstalled the nvidia drivers through Automatix2. I then rebooted and fired up synaptic and searched for the drivers there. To my surprise they were already installed and I had 1024x768 resollution!?! I don't get it but it works. I have another question. Is it possible to install beryl with my old card? The card is an nvidia 32mb tnt2. Thanks for all the replies!

---

### Post by RomeReactor on 2007-05-11
Hi. I suppose it *would* be possible to install beryl; however, that would most likely slow your desktop down to a crawl, seeing as how it would be too GPU intensive for your TNT2. You can certainly try it, though, and see how it goes.

---

### Post by dpzektor on 2007-05-11
Beryl ran kind of unstable even on my Geforce 6200 64MB card. I recently upgraded to a 6600 512MB (Newegg, $80!) and all is incredible. Just some advice in case you feel like getting some more GPU power in Ubuntu eventually. Oh, and TV-Out works too (with some xorg tweaking)

---

### Post by toddr on 2007-05-14
No Joy.:(  I could achieve 1024x768 without accelerated graphics. When I enabled them I only had 800x600. I tried installing them with apt-get, synaptic and automatix and had the same. I'm using the legacy drivers. The nvidia tool in accessories and via the terminal didn't seem to have any settings to change. any ideas?

---

### Post by agkbill on 2007-05-16
I only had 800x600 in the begining but then I added


Option "ModeValidation" "AllowNon60HzDFPModes, NoVertRefreshCheck, NoEdidMaxPClkCheck, NoHorizSyncCheck"


under device section in xorg.conf

---

### Post by toddr on 2007-05-16
I got it working finally! This is what I found after some digging:
[http://ubuntuforums.org/showthread.php?t=432612&highlight=nvidia+tnt2](http://ubuntuforums.org/showthread.php?t=432612&highlight=nvidia+tnt2)
Thanks for all the replies and thank-you smaug067 for the post!

---

