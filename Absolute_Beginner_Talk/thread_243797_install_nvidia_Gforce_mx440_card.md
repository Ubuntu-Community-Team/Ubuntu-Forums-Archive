---
title: "install nvidia Gforce mx440 card"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2006-08-25
I need to install the drivers for my Gforce mx440 card. I have tried the following:
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
This told me that everything was up to date but didn't really indicate the drivers were actually installed. I have installed google earth which went fine but it tells me that my nvidia drivers are not present. This is an old card but on this dual boot machine the card runs google earth on XP just fine so it is certainly within the spec's.
Just need to know how to get the drivers to work.
Many thanks,
tucatts

---

### Post by bswilson on 2006-08-25
I had luck following this procedure:

1) Download and install the deb package:

```
http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu3_all.deb
```

2) Log out and press CTRL+ALT+F1 (so as to get out of the Desktop Environment, i.e. you'll see ONLY the command line)

3) Log in (if required)

4) Run "envy" by opening Terminal or Konsole and typing (quite obviously):

```
$sudo envy
```

5) Choose to install or uninstall the driver (from the textual interface)

---

### Post by Bundles on 2006-08-25
If you have no luck with that, I do have the orig cd with drivers. I can send them to you if you have broadband - dialup will take too long.

---

### Post by Tucatts on 2006-08-25
Hey bswilson, way to go man! Thanks! Great instructions, it went like clock work and Google earth is working like a charm, man I am getting real close to never messing with xp ever again. Printers are my next project but have figured that one out at least part way. Am only going to buy one that I KNOW works right out of the box on Ubuntu, lol. Anyway, will be very glad when I have learned enough to help someone else out like I have been helped.

---

