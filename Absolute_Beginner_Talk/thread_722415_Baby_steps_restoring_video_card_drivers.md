---
title: "Baby steps: restoring video card drivers"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Enixine on 2008-03-12
I installed Ubuntu and for a while my display was holding perfect at something like 1280 x 800.

Then after a day or so, the display suddenly shifted to 640 x 480. I've been told that I should download the drivers for my graphics card again, but I have a few problems with doing that. Hopefully they shouldn't be too tricky.

1. I'm very new to Linux so I don't know how to find out what type of graphics card this computer has. On Ubuntu, how do I find out?

2. Once I do find out, and I can go to the Hewlett Packard site and download them, how do I install them?

Any help would be appreciated.

---

### Post by PmDematagoda on 2008-03-12
Could you please post the model and brand of the PC?

---

### Post by Enixine on 2008-03-12
Sure. It's an old PC.

HP Pavilion desktop, 6653C. To my knowledge I have not replaced or upgraded its video card from the factory-installed model.

Thanks for your help!

---

### Post by PmDematagoda on 2008-03-12
Since the display drivers are Intel I do not think it is necessary to reinstall them.

Try this:-
1) Kill the GUI with:-
```
sudo /etc/init.d/gdm stop
```

2) Reconfigure the X-Server with:-
```
sudo dpkg-reconfigure xserver-xorg
```
Select the options that best suit your PC.

3) Restart the GUI with:-
```
sudo /etc/init.d/gdm start
```

See if that solves your problem.

---

### Post by Enixine on 2008-03-12
Okay, I did the first step, and it shut down the graphical front end and brought up a page in plain text commands:
[list]
[*] Starting anac(h)ronistic cron anacron [ OK]
[*] Starting deferred execution scheduler atd [ OK]
[*] Starting periodic command scheduler crond [ OK]
[*] Checking battery state... [ OK]
[*] Running local boot scripts (/etc/rc.local) [ OK][/list]

Then it stops there on a black screen with white text and a single cursor flashing under the above commands.

I've typed in "sudo dpkg-reconfigure xserver-xorg" and nothing happens. Do I need to restart?

---

### Post by Enixine on 2008-03-12
I hope this isn't against forum policy:

*bump*

---

### Post by PmDematagoda on 2008-03-13
After you kill the GUI, move to a tty by pressing Alt+Ctrl+F2, then enter the commands.

---

### Post by Enixine on 2008-03-14
Hey, that worked! Thanks a lot for your help!

Your instructions allowed me to get my computer to recognize a larger monitor resolution. I'm going with 1280 x 800 for the time being and it's a lot easier on my eyes, I can tell you!

---

