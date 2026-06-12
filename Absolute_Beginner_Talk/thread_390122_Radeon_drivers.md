---
title: "Radeon drivers?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Cruster on 2007-03-21
Hi all,

I've recently installed Kubuntu (for the first time) so I'm truly a novice  :)

My question is from where can I obtain Radeon drivers for an ATI | Mobility&#8482; Radeon® X1400?
Then, how do I install these? Step by step answers would be appreciated feel free to make them as simple as you like ;) 

Sorry if this appears very obvious!

Many thanks in advance.

---

### Post by annda on 2007-03-21
first, i would suggest just changing 'ati' to 'radeon' in you xorg.conf file. this can help (at least in performance of the card). here is how it goes:

back up your xorg.conf by the following command in the terminal:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

if something goes wrong you can restore it by the following command:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

then edit the xserver's configuration file (i'm not good with KDE so i used kate as the text editor, i know there is a simpler one, but i don't remember the name of it):

```
sudo kate /etc/X11/xorg.conf
```

and change ati to radeon. save the file. restart x or reboot.

if this does not work wonders, use this guide to install the binary driver:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

good luck!

---

### Post by Cruster on 2007-03-21
Hi annda.

Thank you very much for your detailed explanation.

I seem to have it all working much better now (completely without knowing what I was doing)
I tried your method & rebooted but the graphics were still slow (jerky redraw when moving an open window about) So I followed the guide you kindly recommended and that seems to have done the trick!

(This all so reminds me of how I felt when faced for the first time with a PC)

Many thanks :)

---

