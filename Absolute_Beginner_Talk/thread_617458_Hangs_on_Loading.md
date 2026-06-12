---
title: "Hangs on Loading"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by ilikecoffee on 2007-11-19
I was able to install 7.1 by taking out my wireless card. But, when I put my wireless card in, it stalls upon loading. The loading bar gets about 80% and just hangs there.

Someone suggested pressing Alt+F1 at the splash screen to watch what's loading. It gets to:

"Starting common UNIX printing system cupsd"

and freezes. Again, only does this with the WiFi card installed. I need to use the wireless with this machine. Can anyone help?

I'm very new to Ubuntu and Linux, so I'm not sure what I'm doing. Thanks in advance.

---

### Post by tyggna1 on 2007-11-19
please post some more info about your system.   Dell?  HP?  Processor?  Hard drive size?  RAM?  Wireless card model?  Other OSes?   We, as a community, really need that kind of stuff to see if we can help.

---

### Post by ilikecoffee on 2007-11-19
It's a Pentium 4 with a Gigabyte mobo, 512 RAM, 250 GB HD.

The Wireless card is Airlink 101 with Realtek 8185 chipset.

Again, Starts just fine without card installed. Freezes with card installed. Haven't tried any other cards, but did try a TrendNet USB WiFi, which didn't get recognized. and so you know, XP recognized them fine which leads me to believe it's a Ubuntu/Kernel issue.

---

### Post by lvleph on 2007-11-19
> **ilikecoffee said:**
> It's a Pentium 4 with a Gigabyte mobo, 512 RAM, 250 GB HD.

The Wireless card is Airlink 101 with **Realtek 8185 chipset**.

Again, Starts just fine without card installed. Freezes with card installed. Haven't tried any other cards, but did try a TrendNet USB WiFi, which didn't get recognized. and so you know, XP recognized them fine which leads me to believe it's a Ubuntu/Kernel issue.

Realtek 8185 chipset  is probably the issue. I press ctrl+alt+f1 and it boots, but when I try to connect to a WEP network my system hangs and I have to hold the power button.

---

### Post by tyggna1 on 2007-11-19
Alright, you're most likely having a driver hang--not serious, but annoying to say the least.

Linux is probably trying to load prism drivers.   You're gonna want to get rid of those first.  To find out exactly what they are type in ```
lsmod
```

Look for something with prism in the name and write down the exact name of all of them.   To remove them, type in:

```
sudo modprobe -r prism<and stuff>
```

Post the entire output of lsmod if prism isn't listed there.

Next, you'll need to install the proper drivers for that wireless card to get it working.   [Here's ]("http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html") a pretty good guide.   It's for Ubuntu 7.04, but it should work.

Post if you have any problems.

---

### Post by ilikecoffee on 2007-11-19
I've actually installed the drivers using the graphic interface for ndiswrapper. "driver present, no hardware"
It seems there is a lot of issues with realtek's chipsets. Is this a known bug?
Just F.Y.I., the drivers for XP changes the user account settings and doesn't allow you to change back under settings. Isn't that a bucket of fun?
But I installed the 98 drivers, so hopefully that problem won't exist.

---

