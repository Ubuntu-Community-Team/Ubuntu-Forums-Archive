---
title: "Nvidia drivers, not reboot friendly"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by the.duckman on 2007-03-24
G'Day,

I've installed the nvidia driver suitable for may card (0.9631).
Everything went well and upon restarting gdm the driver was working sweet al 3d apps went nice and fast and i was happy.

I restart my computer and then I get the infamous "screen(s) were found but no usable configurations" message.

So I altered my xorg.conf back to using the "nv" driver and restart x, Im now back to regular driver with no 3d support. I shutdown x redit xorg.conf change the driver to "nvidia" and start x up again. It works, nvidia splash screen,  3d support, all is good. I restart the machine and Im back to the same old blue screen error message and x wont start.

Ive done all the usual stuff:
>added the DISABLED_MODULES="nv" to linux-restricted-modules-common

>Made sure that the info in xorg.conf shows display modes compatible with my NEC multisync 6FG

>removed any traces of glx drivers

>threatened, pleaded with the computer

> re-read every nvidia on ubuntu "how-to", faw and readme and reinstalled the driver twice.

>googled for solutions to my problem

> tried to use envy and easy ubuntu to do the work for me incase I was doing something wrong

Anyway Im pretty new to xwindows (more of a terminal person) and this driver issue has been vexing me for about 2 weeks now.

I would appreciate *any* help.

My system is an  athon-xp 1600, 256mb ram with nvidia 4600 ti video card. I have a "edgy" instalation with all the  packages and stuff downloaded that are needed for the nvida drivers to properly compile. I am using a wireless NIC.

-dm

---

### Post by martinw89 on 2007-03-24
Try running```
sudo dpkg-reconfigure xserver-xorg
```  Select nvidia and then your appropriate resolution.  That's really weird that on the first boot it works but then after a reboot it doesn't, good luck getting it going.

---

### Post by chili555 on 2007-03-24
I believe the nvidia-glx-legacy package is the more appropriate for your golden-oldie GeForce2 4200ti. I would try removing 0.9631 and installing 0.7184, the legacy driver, especially made for cards like yours (and mine) that are more than six weeks old.

---

### Post by the.duckman on 2007-03-25
Hey Martin,

sudo dpkg-reconfigure xserver-xorg

This utlity seemed familiar from the last time I touched Xwindows (about 5 years ago).

Anyway it didn't help, more to the point it made everything worse, not even the regular nv drivers would get anything going after this procedure, needed to recover a xorg.cong backup I did last week to get the sysem going again.

Anyways The idea seemed good,

Chillie,

My card is the Geforce 4 ti 4600 (not a geforce 2) and The driver I am using is the one recommended by nvidia for this particular card. I have actually tried the legacy driver to see if it helped but the same thing happened.


Still going insane, This issue has consumed so much time I'm actuly wandering if I should try for suse or freespire install instead.... I have a bad feeling If I went to the exent of installing a new distro the same problem would occur.


I am thinking is it possible that the nvidia driver has its own timing/frequency calculation (that does not like my display) . And some how staring x with the nv drivers then stoping gdm then setting the nvida driver the starting gdm  woould invoke the nvidia drivers but with the timing calc of the previous driver or kernal.

long shot...

any thoughts at all?

---

### Post by martinw89 on 2007-03-25
> **the.duckman said:**
> Hey Martin,

sudo dpkg-reconfigure xserver-xorg

This utlity seemed familiar from the last time I touched Xwindows (about 5 years ago).

Anyway it didn't help, more to the point it made everything worse, not even the regular nv drivers would get anything going after this procedure, needed to recover a xorg.cong backup I did last week to get the sysem going again.

Anyways The idea seemed good,
Oops, sorry I hindered.  Have you tried using nvidia-settings yet?  It may have the options for different timings settings.  On mine it only has one option available related to timings, but you may have multiple.  Feel free to totally ignore this also, I already messed up your configuration once :rolleyes:

---

### Post by the.duckman on 2007-03-26
Im not to sure about the monitor being related anymore.

Managed to find a functional xorg.conf from another machine with the same brand/model of display.

Sub in those settings but it still did not help. I am going to try rebulding the nvidia kernal interface again (why not?).

-dm

---

### Post by profXavier on 2007-03-26
Ok, so here is a few options to try.  Using the [Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy"), you will find a way to install your Nvidia drivers.  Two things I have done to get my drivers to work: 
( I initially use the "nv" driver to get into Gnome) 
First, get nvidia-xconfig to setup your xorg.conf.  Remember, you need to do this as sudo.  Second, once you have this, you can use the nvidia-settings to setup your resolutions, etc. Remember, also do this as sudo.  If

 you want to confirm sudo gedit /etc/X11/xorg.conf and compare that to your settings setup in nvidia-settings. (To ensure you used sudo nvidia-settings and the settings saved) If not, copy them directly.

---

### Post by jerrybme on 2007-03-26
I had similar problem with latest drivers from nvidia's website. I found the issues was related to the attempt to load the wrong kernel modules. see Exceptional1's post here:[http://www.ubuntuforums.org/showthread.php?p=2357580#post2357580](http://www.ubuntuforums.org/showthread.php?p=2357580#post2357580)

Editing the /etc/default/linux-restricted-modules-common fixed it for me.

Cheers,
Jerry

---

### Post by the.duckman on 2007-03-28
profXavier,

I thought the ububtu starter guide only provided glx driver instructions. I wish to use the <badword>propietory</badword> drivers from nvidia.

I have tried nvidia-settings before without luck. Good idea though.


jerrybme,

The kernal modules make idea makes a lot of sense.

I have alreadey made a change to /etc/default/linux-restricted-modules-common
however I am not user if I did it correctly, my version of the file reads like a script (scripting language I am not familiar with). and the references say a line with "DISABLED_MODULES" should be present, it's not so I stick it in near the end of the script.

Perhaps I have done this incorrectly and it is the root of my problem.


Anyone,

If somebody has a working linux-restricted-modules-common with the DISABLED_MODULES="nv"  alteration in place that they could post I would appreciate the chance to look over it. I find my file is very different to the others that I have seen posted on line

-dm

---

