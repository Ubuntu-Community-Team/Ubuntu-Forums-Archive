---
title: "downloading from windows for ubuntu"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by moxiot on 2007-03-23
hi there guys. i dont have a network to connect to on my laptop. only whatever is around me at the time. mostly i do all my surfing at school or at internet cafes. ok, so it's clear that i don't have a connection or any ways to get online from my ubuntu partition. i have installed the drivers for the infamous bcm43xx. but obvioulsy it doesn't find the thing even though ndiswrapper -l returns, hardware present. ok, good.
i have posted here before and in other linux forums and either all the replies or how2's i read involve downloading or updating packages. so everytime i read apt-get or downloading i just go nuts because i know it won't work for me since i dont have a connection.
is there any other way to get the friggin bcm43xx to work without using synaptic to install stuff, like the cutter, or updating the kernel.

---

### Post by ichigo on 2007-03-23
You could of course try to download the corresponding deb files in windows, save them in a folder on your hard drive, boot to linux and install them via "dpkg -i *.deb" (after you have changed to the folder where your debs are in). However, doing so you would have to take care of all dependencies. (you could note all packages synaptic would install)

Another way would be to connect your laptop via LAN instead of WLAN, if you can do this somewhere. Then you could follow the howtos...

---

