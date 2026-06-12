---
title: "Newbie needs help with display:  compiz and borders"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by ctothebizza on 2008-04-07
Hi guys.  I am completely new to this, so please bare with me.  I just installed ubuntu today, and followed all of the prompts during installation.  I am having two problems with my display.  1.  When I put my mouse above the window borders to close or minimize a window, the bar disappears.  It's kind of frustrating, so if you could help me that would be great.  2.  I was wondering how I install all of the cool compiz fusion effects.  I got my windows to wobble, but I don't see any other options anywhere.  I read the guides about this, but they are all for ubuntu 7.10.  I have 8.04 I think, so do I use the same method to turn it on?  Sorry, I hope this isn't dumb, but I don't want to mess up the installation since it took about 6 hours to get to the point I'm at! :)  Thanks in advance!!

Oh, my computer has

AMD X2 5200+
2 gb Ram
onboard nVidia graphics.

---

### Post by twist2b on 2008-04-07
obviously you are using feisty..
BEST FIX!
before boot in GRUB goto recovery mode of the partition you load what you are using.
when its booted up type:
apt-get update
then
apt-get install nvidia-glx-new
it installs all the stuff that makes nvidia run SMOOTH and PERFECT
then type
dpkg-reconfigure xserver-xorg
now RIGHT away it shows which drivers its using.... if your using feisty its prob on VISA
if your using GUSTY your prob using nv
NOW use the newly added "nvidia"
follow all the steps and boot and it should be fixed. if not:
run these:
dpkg-reconfigure --priority=low postfix (there is a black window issue that is removed by this)
sudo nvidia-xconfig -add-argb-glx-visuals -d 24
this will fix no window boarders..... might have to add it to startup.

---

### Post by Moop on 2008-04-07
Install the compizconfig-settings-manager and the fusion icon from the repositories. Here is the guide I used for compiz settings and effects. 
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#)

---

### Post by diablo75 on 2008-04-07
In terminal:

```
sudo apt-get install compizconfig-settings-manager
```

This will add a new advanced appearance control panel to your appearance applet, as well as your Preferences menu.

I don't know what to do about your title bar disappearing.  Mine flickers a little when I pass my mouse over the buttons in the top right, but other than that it stays stable.  So I can't help you with that first question.

---

### Post by diablo75 on 2008-04-07
> **twist2b said:**
> obviously you are using feisty..
BEST FIX!
before boot in GRUB goto recovery mode of the partition you load what you are using.
when its booted up type:
apt-get update
then
apt-get install nvidia-glx-new
it installs all the stuff that makes nvidia run SMOOTH and PERFECT
then type
dpkg-reconfigure xserver-xorg
now RIGHT away it shows which drivers its using.... if your using feisty its prob on VISA
if your using GUSTY your prob using nv
NOW use the newly added "nvidia"
follow all the steps and boot and it should be fixed. if not:
run these:
dpkg-reconfigure --priority=low postfix (there is a black window issue that is removed by this)
sudo nvidia-xconfig -add-argb-glx-visuals -d 24
this will fix no window boarders..... might have to add it to startup.

Hmmm....

---

### Post by ctothebizza on 2008-04-07
> **diablo75 said:**
> In terminal:

```
sudo apt-get install compizconfig-settings-manager
```

This will add a new advanced appearance control panel to your appearance applet, as well as your Preferences menu.

I don't know what to do about your title bar disappearing.  Mine flickers a little when I pass my mouse over the buttons in the top right, but other than that it stays stable.  So I can't help you with that first question.

Awsome!! That was much easier than I had anticipated!  I now have access to the compiz settings.  It might take a while for me to figure them out, but they work.  As for the disappearing bar.  I don't know what to do.  Thanks for the suggestion twist2b, but I think that is a little over my head. :(  Thanks for the guide Moop!  I'll try and work my way through it.  Thanks All!

---

