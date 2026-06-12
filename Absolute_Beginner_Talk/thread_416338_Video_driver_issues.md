---
title: "Video driver issues"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Soverign on 2007-04-21
Hi all,

So I'm pretty new to linux, been sort of playing around with edgy on my dual boot system for a while...& I've managed to mess up my system :-). Yay!

Basically, I've been wanting to install Beryl or something to make my computer look really sweet, but my comp doesn't pass the first step: glxinfo returns direct rendering: No.
I seem to remember that I tried this earlier and it said yes, so it's possible simply reinstalling would fix the problem.

I'm running on an ATI 9800 PRO. I think it has direct rendering ;)
Anyway, so I tried to install the new ati drivers as instructed by the ATI drivers link found on the Beryl installation page ([http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)) & now I restart my comp and...voila, after the grey loading screen, I get a black screen with an occassional white box that reads:
Hz ?

So my refresh rate isn't defined?

Ok...so what do I do about it? 

Any help would be awesomely appreciated :-)

---

### Post by mikewhatever on 2007-04-21
You can try a different way of installing the driver [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Envy also has an option of reconfiguring xserver for you.
Yet another option would be to boot into recovery mode and look into xorg.conf by typing > sudo nano /etc/X11/xorg.conf
Things would be even easier if you have a backup of xorg file. To restore the original from that backup type > sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

