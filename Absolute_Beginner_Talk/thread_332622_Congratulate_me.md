---
title: "Congratulate me"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-01-06
I got ubuntu to install on my pc with a help of two guides here.
Booting to Ubuntu required me to pick recovery, then type exit to get into ubuntu.
everything appeared to work fine.
Until I went and installed the ati drivers from the file menu screen. Sorry forgot the name and I am at work.

Now it does not boot even in recovery I get to the prompt and am unable to do a thing.

:) I crashed my system with the first install.

Note to self do not install ati drivers for your ati card.

btw I have an ati x700 card. Tempted to yank it out but my xp games require it, what to do what to do.

Reason I installed drives was my video screen is 1400x900 and i only was getting 1000x 800 or something to that effect.

Any suggestions what to do to recover or do I just reinstall the whole thing again?

---

### Post by taurus on 2007-01-06
When you get to a prompt in the recovery mode, edit your /etc/X11/xorg.conf and replace whatever "Driver" you are using right now back to"ati".

```
nano -w /etc/X11/xorg.conf
```
Save the change by <Ctrl>x.  Then, see if X is working again with

```
startx
```
Otherwise, reconfigure X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by rbhigday on 2007-01-06
woot, thanks was expecting to have to reinstall, will try that when I get home from work this evening and post the results.

---

### Post by rbhigday on 2007-01-06
> **taurus said:**
> When you get to a prompt in the recovery mode, edit your /etc/X11/xorg.conf and replace whatever "Driver" you are using right now back to"ati".

```
nano -w /etc/X11/xorg.conf
```
Save the change by <Ctrl>x.  Then, see if X is working again with

```
startx
```
Otherwise, reconfigure X again with

```
dpkg-reconfigure xserver-xorg
```

Ok I did all this and now it does not detect my monitor. 


will try to use generic monitor and see what happens, wish me much

---

### Post by kill4killin on 2007-01-06
The ATI drivers for linux pretty much just flat out are bad...I installed them and thankfully they worked fine on my mobility X1400 but I have heard a lot of stories like yours from people having the same problems with the driver. I personally can't wait until they release a better one...

---

### Post by taurus on 2007-01-06
Pick **vesa** for the driver of your graphic card then...

---

### Post by Sasa_Ivanovic on 2007-01-06
congratulationz !!!!

---

### Post by rbhigday on 2007-01-06
> **taurus said:**
> Pick **vesa** for the driver of your graphic card then...

Ok that worked, but strangly that what i was to begin with :confused: ](*,) 

Thanks for the help everyone

---

