---
title: "Why is it when I try to enable Desktop Effects to &quot;Extra&quot; it always goes back 2 None"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-25
Help please...?

---

### Post by frup on 2007-12-25
What kind of graphics card do you have?

Did you install via CD or upgrade from 7.04?

Have you checked in synaptic whether all the compiz packages are installed properly?

---

### Post by hilariousness16 on 2007-12-25
> **frup said:**
> What kind of graphics card do you have?

Did you install via CD or upgrade from 7.04?

Have you checked in synaptic whether all the compiz packages are installed properly?

 ATI Radeon XPRESS 200M

I installed from CD, not upgraded, I just got gutsy like a week ago?

How do I know if it is installed correctly?

NOTE: Compiz was working yesterday with the cube thing and all, but it won't let me go to "Normal", "Extra", and "Custom".

---

### Post by hilariousness16 on 2007-12-25
ARG this is driving me nuts.:KS

---

### Post by spiderbatdad on 2007-12-25
have you tried gnome-compiz-manger?```
sudo apt-get install gnome-compiz-manger
```

```
sudo apt-get install emerald
```

```
sudo apt-get install compizconfig-settings-manger
```


you should probably get rid of xserver-xgl if you installed it.

---

### Post by hilariousness16 on 2007-12-25
how do I ge rid of xserver lol

---

### Post by spiderbatdad on 2007-12-25
you dont. I meant the package xserver-xgl in synaptic. if you installed it

---

### Post by hilariousness16 on 2007-12-25
Er.. Didn't really do anything...

---

### Post by hilariousness16 on 2007-12-25
:)

---

### Post by spiderbatdad on 2007-12-25
have you looked into envy at all? That should really screw up your environment for awhile.

---

### Post by hilariousness16 on 2007-12-25
Should I install ENVY?

---

### Post by spiderbatdad on 2007-12-25
you can read about it here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)    get the all.deb package if you do

---

### Post by hilariousness16 on 2007-12-25
I installed ENVY and nothing special happened

No HOPE!

---

### Post by spiderbatdad on 2007-12-25
after unpacking it from your desktop, i believe you have to check the restricted drivers manger. it is not possible that nothing special happened if you installed it and ran it. Then try to enable "custom"

---

### Post by gupta_sumesh63 on 2007-12-26
Try the following.
start compiz. (through appearance->extra.)
then open the session manager(preference), and save the current session.
Restart the computer.
I think it'll stay.

---

### Post by shareMenaPeace on 2007-12-26
hilarious, use this HOWTO

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by hilariousness16 on 2007-12-26
what do you mean when you said "save the current session":lolflag:

---

### Post by hilariousness16 on 2007-12-26
UUGGGHHHHH, Do I need a new graphics card?

---

### Post by shareMenaPeace on 2007-12-26
Why dont you use the howto i posted ..the grafic card is supported ...

---

### Post by hilariousness16 on 2007-12-26
> add it to the compiz white list, and clear the blacklist pci Ids variable *Recommended*

sudo gedit /usr/bin/compiz

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

# blacklist based on the pci ids 
# BLACKLIST_PCIIDS="$T"
BLACKLIST_PCIIDS=""


I don't know what to do with the
```
# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"
```

---

### Post by shareMenaPeace on 2007-12-26
moment, this is not nessassry ..only for glxinfo/...


what you get with

```
fglrxinfo
```

---

### Post by Ripfox on 2007-12-26
[http://ubuntuforums.org/showthread.php?t=548785](http://ubuntuforums.org/showthread.php?t=548785)

This is how I did it with my GF's 200m. It works.

---

### Post by hilariousness16 on 2007-12-26
bump:popcorn:

---

### Post by hilariousness16 on 2007-12-26
```
brandon@brandon-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

```

---

### Post by shareMenaPeace on 2007-12-26
Can you pleas epost the xorg.conf again, thx

---

### Post by shareMenaPeace on 2007-12-26
somehow you have a old driver i belive ...
mine looks like this

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X2300
OpenGL version string: 2.1.7059 Release


```

So if someone helps you tell him this ... i need to sleep now sorry, hope yoe will sort it out, cu later ....

---

### Post by spiderbatdad on 2007-12-26
i think the biggest problem has been NOT rebooting in between installing drivers and attempting to enable desktop effects.

---

### Post by hilariousness16 on 2007-12-26
Is it really that old, I got the laptop like 1 year ago.

---

### Post by hilariousness16 on 2007-12-26
SHAREMENA IF YOU ARE THERE SHOULD I GET A NEW DRIVER

and where's your scary avatar, can I have it? lol:lolflag:

---

### Post by hilariousness16 on 2007-12-26
Nvm, I can't, the computer store said it is too diffacult to remove the driver:(

---

### Post by shareMenaPeace on 2007-12-26
OH i belive the avatar is lost now ...  hmm you should uninstall ati drivers ...boot than start failsafe ....than logout into gnome again ...than run envy again and see with above command what driver you has than ...

i know there a ways to completly uninstall drivers ..maybe its broken ...i hope someone with more knowledge helps zou sooon......

---

### Post by hilariousness16 on 2007-12-26
Wait, are you saying your a noob? :lolflag:

---

### Post by shareMenaPeace on 2007-12-26
Welll after 1 yeard ubuntu i start to understand how linux works and where stuff is, what i need to run things, what i need to look at ...well can be improved ofc, well i dont know :)

I just think omg all the peopel who have not so big understanding of systems, what do they / must be really hard ..itf its even for me lol

But who cares, what counts is that you work on it, cheers

:guitar:

---

### Post by shareMenaPeace on 2007-12-26
Rightnow you have a big learing curve going up...in a few weeks you become used to it, and when you think back to today you will realise that you learned something and that its good ..  ok i say not everything is logic to me in linux or bsd, but i see progress ... and thsi is good and allready ubuntu is partly much greater than vista, vista is currently just still easyer to setup ... but its still the old windows what you realize soon ... but to setup desktop gadgets and docks in vista is really easy, here itt needs improvements, but compiy ofc allready pwny vista or anything else.... in 1 or 2 years ubuntu will completly outrage any other system ....

---

### Post by MasterJS on 2007-12-26
I have that video card and the only way i EVER got it running in 7.04 was with XGL, without it i never got it running. Anything else, anything that had to do with configuring the xorg.conf file always screwed up my system and would force me to reinstall. For ATI cards, the only thing that works at the present moment is XGL. 7.10 fixed this by helping with the installation of the driver and xgl, but in 7.04, your best bet is to search these forums for "ATI Radeon Xpress 200M XGL". By searching that, there is a forum and a how to that someone posted up that really helped me during my time with Ubuntu Feisty Fawn 7.04.

---

### Post by hilariousness16 on 2007-12-26
ok ty everyone

---

### Post by hilariousness16 on 2007-12-26
UGH im just going to reinstall ubuntu:confused:

---

### Post by Ripfox on 2007-12-26
Dude...if you reinstall, PLEASE use the link I posted earlier...IT WORKS. It would be better to reinstall then use that link on a fresh install.

---

### Post by abicash on 2007-12-27
> **spiderbatdad said:**
> have you tried gnome-compiz-manger?```
sudo apt-get install gnome-compiz-[COLOR="Red"]mange[/COLOR]r
```

```
sudo apt-get install emerald
```

```
sudo apt-get install compizconfig-settings-[COLOR="Red"]mange[/COLOR]r
```

.

i think there's a typo above!
*manager

---

