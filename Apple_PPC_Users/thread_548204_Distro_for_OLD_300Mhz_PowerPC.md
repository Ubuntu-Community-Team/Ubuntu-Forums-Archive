---
title: "Distro for OLD 300Mhz PowerPC?"
date: 2007-09-11
forum: Apple PPC Users
---

### Post by GSF1200S on 2007-09-11
My friend has an old iMac with a 300Mhz ppc processor and 64mb of RAM. Im looking for a distro that uses some kind of X that will still run decent. His iMac had Mac OS9 and OSX, so im sure theres bound to be a Linux alternative.

His OS9 went to crap, and they want to charge him 150 to get it working (not worth it). I was thinking about an Ubuntu-Lite install, but i dont know how the repos are or if it needs more ram than that. 

Hes never used Linux, and he seems to be nervous to give it a shot. I want something thats fairly easy, but will run fast on his hardware. I only have a week to get this done before he changes duty station (navy), so getting more RAM would prolly be a no.

Any ideas?

---

### Post by kerry_s on 2007-09-11
geez, you might as well ask for are right arms. :lolflag:

anyway's with those specs there's not much hope, your going to have to compromise somewhere. i would recommend you do a custom debian install.

[http://cdimage.debian.org/debian-cd/4.0_r1/powerpc/iso-cd/debian-40r1-powerpc-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/powerpc/iso-cd/debian-40r1-powerpc-businesscard.iso)

you want to install the base, that means when it comes to package selection, uncheck them all.

after the base is installed and it boots into the system(no gui yet)log in as root
apt-get install xorg gdm synaptic icewm rox-filer leafpad dillo
reboot(ctrl+alt+delete)
select icewm in the session menu and login as your regular user.
open synaptic and get what ever else you want.

being new he's going to need to read up on linux, it might be tough going at first.

---

### Post by GSF1200S on 2007-09-11
> **kerry_s said:**
> geez, you might as well ask for are right arms. :lolflag:

anyway's with those specs there's not much hope, your going to have to compromise somewhere. i would recommend you do a custom debian install.

[http://cdimage.debian.org/debian-cd/4.0_r1/powerpc/iso-cd/debian-40r1-powerpc-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/powerpc/iso-cd/debian-40r1-powerpc-businesscard.iso)

you want to install the base, that means when it comes to package selection, uncheck them all.

after the base is installed and it boots into the system(no gui yet)log in as root
apt-get install xorg gdm synaptic icewm rox-filer leafpad dillo
reboot(ctrl+alt+delete)
select icewm in the session menu and login as your regular user.
open synaptic and get what ever else you want.

being new he's going to need to read up on linux, it might be tough going at first.

Yeah, I know thats asking alot. That sounds like it might be the ticket though. Hes not really going to use it for much.. the main things are viewing pictures and browsing the web. Dillo is definitely fast, but do you think Opera 7 or even 6.0 would be ok on this system? I know Fox and even Opera 9 uses way to much ram, but maybe a decent tabbed browser. If not, he can live with it- im just trying to make a good impression so hell stick with it...

**edit** Ill be doing the install and configure, so hell just need to get used to the file system and how it looks... Ill have to get used to IceWM myself... Does the debian repos carry alot of stuff for IceWM, or does it integrate well with Gnome apps...

---

### Post by kerry_s on 2007-09-11
you can try a full browser, might be slow starting, but should be fine after that. remember in debian firefox is iceweasel> apt-get install iceweasel

icewm is well documented so you should be okay there, ive had no problems with gnome apps in icewm, they both use gtk. you have to think light if you want to get the most out of that beast. just use the first couple of installs as a kind of test bed, get the feel of the rig, see what works and what doesn't, write it down. i think xfce4 is easier but i'm not sure about the speed for that rig, maybe give that a try to. main thing just get the install on there than you can run different setups to find a middle ground for speed and function.

---

### Post by indelible on 2007-09-11
I installed ubuntu PPC server on my powerbook G3 400mhz and then installed X and xfce, and its quite useable for browsing and mp3s and stuff, but then, it has 320mb of ram which is a far cry from 64 when you're talking about X. hope you get something suitable set up.

---

