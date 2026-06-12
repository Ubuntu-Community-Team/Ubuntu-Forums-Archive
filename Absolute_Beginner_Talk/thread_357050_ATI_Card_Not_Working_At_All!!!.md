---
title: "ATI Card Not Working At All!!!"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Mydrid on 2007-02-09
I am returning to the world of Linux after a lengthy hiatus, though I am still pretty much an absolute Newbie. I have downloaded and installed Ubuntu on my system. The installation seemingly works fine. When I boot up, I get the nice orange Ubuntu loading screen, followed by an error saying that my Xserver is not set up properly, which sends me into a text console without ever giving me a glimpse of any GDU. I have tried several guides to install drivers for my ATI Radeon 9250, but to NO avail. the ATI installer seems to start to work when using the (sudo) 'sh ati-driver-installer-8.28.8.run' command. The package begins to extract and then tells me that there has been a substitution error and I am back to square 1. I have tried my old NVidia card, but I get even worse results with that. I am surprised that this Ubuntu release does not work 'out of the box' with a Radeon 9250 card, as it is seemingly extremely popular. I have also tried following the 'How To on ATI drivers' by Maqi, but that gets me absolutely nowhere. Are there any other things that I can try just so that I can see some kind of GDU. I know that the soul of Linux is in the code, but I would love to be able to actually use my computer efficiently, without having to input 50 million lines of code for every action. Maybe I am just tainted by the fuzzy awful Microsoft look, but Ubuntu is supposed to 'Just Work'. Please give me some tips if there are any to be had. Thanks.

---

### Post by renzokuken on 2007-02-09
that card worked out of the box for me......

anyways when it crashes back to the terminal screen, do this

```
sudo nano /etc/X11/xorg.conf
```

go down to the Section "Devices" part of the file and make sure that the Driver line is using vesa......it should look like

```
Driver    "vesa"
```

if there is something else written there, then simply delete it and put [color=red]vesa[/color] in......

the press Ctrl+X, Y and enter to save and exit, then reboot

```
restart
```

see how that works

---

### Post by Mydrid on 2007-02-10
Thanks for the suggestion. It worked to some extent, but there were still big issues. In the end, I did a reformat and fresh install. As if by magic, the problem was solved. Thanks for the tip, though!

---

