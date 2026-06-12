---
title: "Massive mistake on installing Ubuntu studio"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Ludford on 2007-07-19
On installing ubuntu studio I accidentally hit Enter at the choose what to install options, it is now on a progress bar and I cannot get back.

Can I install this software later? (I want to install everything)

---

### Post by rickycodie on 2007-07-19
yes you can install from the repositories, anything that you need.

---

### Post by Ludford on 2007-07-19
Thank god for that, I had a sinking feeling I was going to have to delete all my partitions and start again.

EDIT: GOD DAMMIT, I just did it again at the resolution install screen, can I install 1200x800 later?

---

### Post by Ludford on 2007-07-19
"Failed to start the X server (your graphical interface). it is likely that it is not set up correctly"

I get this when choosing to boot linux from my OS selecter

---

### Post by rickycodie on 2007-07-19
i think the command is 

sudo dpkg /etc/X11/xorg.conf

the command is case sensitive.

---

### Post by Ludford on 2007-07-19
I tried "sudo dpkg-reconfigure xserver-xorg" but intel is not on the list, I made a thread about it.

---

### Post by rickycodie on 2007-07-19
yeah i just came back to tell you to use that command, what kind of driver do you have?

---

### Post by Ludford on 2007-07-19
not sure but the card is an Intel GMA 950

---

### Post by rickycodie on 2007-07-19
try the i86 driver for now, then follow this to get the proper driver

[http://www.intel.com/products/chipsets/gma950/index.htm](http://www.intel.com/products/chipsets/gma950/index.htm)

---

### Post by Ludford on 2007-07-19
i86 is not on the list either, just i123, i1740 and i810

---

### Post by Ludford on 2007-07-19
I installed i180 but after the colour bit select screen it says.

Xserver-Xorg postinst warning: overwriting possibly-customized con figuration file; backup in /etc/X11/xorg.conf.20070719202701.

what should I do now?

I tried reboot but it says need to be root

EDIT: holy ****, the login screen came up and its working!, am I all set? can I start using linux, theres a buble that says "new restricted drivers in use" shall I ignore that?

---

### Post by rickycodie on 2007-07-19
no install them they are the drivers that you need.

---

### Post by Ludford on 2007-07-19
and to do that I type

sudo apt-get install xserver-xorg-video-intel

Don't I?

---

### Post by rickycodie on 2007-07-19
look on your system tray there should be a little green chip, click that and install those drivers.

if not it's system>admin>restricted drivers, i think, i'm at work and not on my box.

that should fix it for you.

---

### Post by Ludford on 2007-07-19
that wasn't about my card, it was talking about my wireless internet

---

### Post by rickycodie on 2007-07-19
have you tried the link?  otherwise i'm dry.

---

### Post by Ludford on 2007-07-19
cool, so linux can use the same drivers for my card windows uses

EDIT: I can't seem to see a download link, also I'm guessing that the reason I can't seem to find an option for desktop effects is that I don't have the correct drivers

---

### Post by rickycodie on 2007-07-19
look for the linux driver

[http://www.intel.com/products/chipsets/gma950/index.htm](http://www.intel.com/products/chipsets/gma950/index.htm)

edit:sorry do you have 7.04 installed (fiesty fawn)?

---

### Post by Ludford on 2007-07-19
I have Ubustu, which I believe is the exact same but with a different theme

EDIT; I am going to try the 945GM drivers, Linux device manager says this is the card I have, yet XP insists it is a 950

EDIT2: Ok, now I'm really confused, I have downloaded the drivers but there is no executable (or anything that look like it could be one) just a bunch of random files and folders

---

### Post by rickycodie on 2007-07-20
does the package you downloaded end with a tar.gz? if it does then it needs to be compiled. there should be instructions in the package, if not go to 

[www.howtoinstallanythinginubuntu.com](www.howtoinstallanythinginubuntu.com)

and click on the tar.gz  howto.

---

