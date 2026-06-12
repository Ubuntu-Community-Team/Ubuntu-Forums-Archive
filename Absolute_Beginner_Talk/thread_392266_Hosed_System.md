---
title: "Hosed System"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by falk3r on 2007-03-24
'ello, new to ubuntu here:

ubuntu 6.10, fully updated
ATI Radeon x700
Dell 1702FP monitor

Initial Problem: ubuntu was only offering 640x480, 800x600, & 1024x768 when I was looking for a higher resolution on my monitor.

Initial Attempt: Synaptic Package Manager --> Installed xorg-driver-fglrx, used terminal command "sudo dpkg-reconfigure xserver-xorg", and  followed on-screen prompts to the best of my ability. Researched horiz-vert refresh rates, and the such. Once this was complete, I rebooted and now my monitor is getting no signal from my video card.

Could someone refer me to a thorough walkthrough of this? Or, if you have the time... walk me through 1) resolution of hosing my system and 2) adding additional resolution support?

Many thanks,
 - falk3r

---

### Post by lamalex on 2007-03-24
is getting 0 signal? as in, its not even displaying bios and boot info? or can you get to a terminal. <control alt f1>. if you can get to a terminal try typing this
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by falk3r on 2007-03-24
It displays the bios, boot information; but once the OS loads, the monitor goes black... and the LED on the monitor changes from green to yellow to indicate "no signal". As far as I can tell, ubuntu is there in the background... I just can't see it ;)

I can still boot from the LiveCD, would this give me access to the appropriate configuration files to edit? If so... uhm, how?

Many thanks,
 - falk3r

---

### Post by falk3r on 2007-03-24
Solution found:

In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

Thanks Phasmagon,
 - falk3r

:guitar:

---

