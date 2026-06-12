---
title: "[SOLVED] Help me decide..."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Gasmask14 on 2007-12-11
I just inherited a old desktop and want to run ubuntu on it. One of my friends runs Ubuntu and swears by it. He let me borrow a live CD and I think I would like it better than plain old XP. He showed me some basics on Linux but I am not sure what version I should download. Should I download Gusty as a new user or should I download the LTS Dapper? Which would be easier and which one has better features?

Thanks

P.S.

Specs:
amd 3200+ 64 processor, 1 GB of DDR, 160 GB HD, NVIDIA Geforce FX5200 XT video card w/ 128 MB dedicated

With this could I run beryl/compiz fusion?

---

### Post by Pumalite on 2007-12-11
Your video card could be a problem. Do a 'Search'

---

### Post by Pumalite on 2007-12-11
I found this:
[http://ubuntuforums.org/archive/index.php/t-136919.html](http://ubuntuforums.org/archive/index.php/t-136919.html)
So, I might be wrong.

---

### Post by Gasmask14 on 2007-12-11
Cool, so it might work w/ compiz (still not sure what XGL is). What OS would best work on my computer though?

---

### Post by annda on 2007-12-11
forget dapper, get gutsy or at least feisty. it will work fine on your computer. especially if you want to use all the flying windows and desktops, get the latest versions -compiz is much easier to setup there.

[XGL]("http://en.wikipedia.org/wiki/Xgl") is the gizmo technology that will let you run compiz, to put it simple. 

also, search some more to find out about the 64-bit version. some people have reported better results running the 32-bit ubuntu on their 64-bit machines but my info can be outdated, since i don't own one and never had a chance to test.

---

### Post by ardchoille42 on 2007-12-11
1) I would install Gutsy. Dapper is a Long Term Support release, but it's quite old now and Gutsy is stable.

2) Doing an upgrade from Gutsy to Hardy (the next release and will also be an LTS release) will be much easier than upgrading from Dapper > Edgy > Feisty > Gutsy > Hardy - upgrades must go from release to release, one at a time.

3) Being newer, Gutsy provides a better computing experience, IMHO.

---

### Post by Gasmask14 on 2007-12-11
Will my computer support a 64 bit OS? Is it easier to learn on?

---

### Post by dpar on 2007-12-11
Your video card won't be a problem. I'm running the FX5200 and use Compiz with no problem.

---

### Post by Gasmask14 on 2007-12-11
Will I have to do anything special to get it to work with compiz or will it work "out of the box"?

---

### Post by aysiu on 2007-12-11
> **Gasmask14 said:**
> Will I have to do anything special to get it to work with compiz or will it work "out of the box"?
This is how you do it:
[http://www.psychocats.net/ubuntu/desktopeffects](http://www.psychocats.net/ubuntu/desktopeffects)

---

### Post by Gasmask14 on 2007-12-11
Thanks

---

### Post by oeolycus on 2007-12-11
I agree with the other posts. Install Gutsy, check out the effects and experiment with the applications. Unless you have major problems (and then you can revisit the decision), it will do everything you need. 

By jumping in to Ubuntu (Gnome or KDE) you will learn to use those interfaces, just like you once had to learn XP or whatever other OS you've used before. Eventually, if you pursue it, you will have enough experience with the command line and Linux in general that you can revisit your OS decision. Who knows if you'll be a major tweaker or content Ubuntu user ... no reason to decide now :)

Just install and start messing around!

---

### Post by Gasmask14 on 2007-12-11
Does Gutsy include Compiz or do I have to install it thru Synaptic?

---

### Post by philinux on 2007-12-11
It's enabled by default if your hardware supports it.

---

### Post by Gasmask14 on 2007-12-12
I finally got some freee time and installed Gutsy. When I tried to enable destop effects/compiz I got the message "Desktop effects could not be enabled". Is this from my drivers or my video card?

P.S.
When trying  to enable desktop effects It made me download a newer genaric Nvidia driver vs the one that got installed w/ the CD. I later reverted back to my other driver and neither worked.

If anyone else has this card what did you do?

---

### Post by Mze on 2007-12-12
You might have to uninstall your nvidia drivers and restart the process.

I used this [Envy]("http://albertomilone.com/nvidia_scripts1.html") script to get an FX5200 to work.

Pretty straight forward instructions on the guys website.

---

### Post by dpar on 2007-12-13
I didn't have to use envy, I just installed the restricted drivers via the restricted drivers manager. Also, make sure you download ccsm (compizconfig-settings-manager). It's in the repos.

---

### Post by Gasmask14 on 2007-12-13
I got it working once I reinstalled my restricted drivers and downloaded the compiz manager. Thanks for the help.

---

