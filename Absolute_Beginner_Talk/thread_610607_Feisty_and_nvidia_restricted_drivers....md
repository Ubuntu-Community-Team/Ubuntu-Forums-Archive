---
title: "Feisty and nvidia restricted drivers..."
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by thenailedone on 2007-11-12
Installed Feisty last night... (still waiting for Gutsy)...

Went to the restricted drivers section and tried to enable the nvidia drivers... gives me a dialogue asking if I would like to continue... click on enable and... nothing happens, the drivers stay disabled...

(Did a couple of searches and all I am getting is a typical response of "remove what you have and get new stuff" kind of answers... or very specific Gutsy related info... no one loved the Feisty Fawn anymore :( )

---

### Post by Shinbu-Otaku on 2007-11-12
Is your computer connected to the internet? As the drivers need to be downloaded before installation.

If this solves the problem, press ctrl+alt+backspace to restart the desktop, and you should see a screen with the NVidia logo on

---

### Post by thenailedone on 2007-11-12
> **Shinbu-Otaku said:**
> Is your computer connected to the internet? As the drivers need to be downloaded before installation.

If this solves the problem, press ctrl+alt+backspace to restart the desktop, and you should see a screen with the NVidia logo on

(Not on the net... yet) Thing is... as far as I can tell the drivers are their (In the Packet Manager they seem to be their and under Restricted Drivers)... they just don't want to be enabled... 

(Please bear with me... I was a n00b with Linux when I tried it in '96... staued a n00b when I tried it in '02 and a bigger n00b now in '07)

---

### Post by thenailedone on 2007-11-13
> **Shinbu-Otaku said:**
> **Is your computer connected to the internet? As the drivers need to be downloaded before installation.**

If this solves the problem, press ctrl+alt+backspace to restart the desktop, and you should see a screen with the NVidia logo on

I acknowledge Shinbu-Otaku's wisdom!  After having to re-install Feisty (long story, removed all of the graphics drivers and killed X... to much of a noob to know how to recover) I again tried the restricted drivers while in the live CD and got the error message about not being able to connect to the net... (pity it hadn't given me this error message once it was installed :( )... I guess my first mission is to get my internet back and running...

---

### Post by Jimmyfj on 2007-11-13
Your computer needs to be connected to the internet while enabling the restricted driver. All files in restricted drivers manager AND in both Add/remove programs and synaptic needs to be downloaded from the internet unless you have the software on a DVD set

---

### Post by Shinbu-Otaku on 2007-11-13
> **thenailedone said:**
> I acknowledge Shinbu-Otaku's wisdom!  After having to re-install Feisty (long story, removed all of the graphics drivers and killed X... to much of a noob to know how to recover) I again tried the restricted drivers while in the live CD and got the error message about not being able to connect to the net... (pity it hadn't given me this error message once it was installed :( )... I guess my first mission is to get my internet back and running...

i had a funny feelin this was the case, at least you now know what to do, and once you are connected to the net, there shouldnt be a problem enabling the nvidia drivers.

glad to help :)

p.s. im still a bit of a noob, i woulda done the same (wipe it all off) i had X crash on me when i last upgraded, so i just wiped it all and requested the new CD, aint had a problem since *touch wood*

---

### Post by TeaSwigger on 2007-11-13
> **thenailedone said:**
> I acknowledge Shinbu-Otaku's wisdom!  After having to re-install Feisty (long story, removed all of the graphics drivers and killed X... to much of a noob to know how to recover) I again tried the restricted drivers while in the live CD and got the error message about not being able to connect to the net... (pity it hadn't given me this error message once it was installed :( )... I guess my first mission is to get my internet back and running...

And after you get online & the restricted drivers installed and reboot, it may be a good idea to double-check the /etc/X11/xorg.conf file and see that it's actually using them; if I'm remembering right, it installed but kept using the old one. I changed 'nv' to 'nvidia' in xorg.conf, restarted and bingo, primo graphics since.

EDIT: should note, this concerns just my experience with Feisty and nvidia legacy restricted drivers, ymmv.

---

