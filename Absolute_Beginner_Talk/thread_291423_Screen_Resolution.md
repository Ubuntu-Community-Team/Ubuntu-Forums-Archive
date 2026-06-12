---
title: "Screen Resolution"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Antexter on 2006-11-02
I cant go above 1024x768 and its really annoying me.
How can i change it?

---

### Post by Kateikyoushi on 2006-11-02
Try to configure X again.
Use this command.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bigken on 2006-11-02
have you tried sudo dpkg-reconfigure xserver-xorg and using the space bar to select your desired resolutions


also do you have the corect video driver installed ?

---

### Post by Antexter on 2006-11-02
i tried sudo dpkg-reconfigure xserver-xorg dont have a clue what im doing i went all through it etc...

It has my graphics card on it because it shows it when i type in sudo dpkg-reconfigure xserver-xorg my graphics card is ati sapphire 9600

---

### Post by bulldog on 2006-11-02
> **Antexter said:**
> i tried sudo dpkg-reconfigure xserver-xorg dont have a clue what im doing i went all through it etc...

It has my graphics card on it because it shows it when i type in sudo dpkg-reconfigure xserver-xorg my graphics card is ati sapphire 9600

It recognized your ATI-card,but did you install the drivers?
This is not automaticly done by Ubuntu.

---

### Post by Antexter on 2006-11-02
not what i know of, I've just looked on ati website and i cant find any for 9600.

---

### Post by bulldog on 2006-11-02
Well search the forum for a link or look in the Wiki.

To get a better resolution you have to install drivers for your graphics.

---

### Post by vince vega on 2006-11-02
I've been having the same problem with my Nvidia card.

---

### Post by Kateikyoushi on 2006-11-02
I got high res even with the default "nv" driver so I doubt it is a driver issue in vince's case.

---

### Post by vince vega on 2006-11-02
Kateikyoushi, Any idea as to how I can fix this?

---

### Post by wadeall on 2006-11-02
If anyone happens to be  using the Viewsonic VM 2025wm monitor, there is a problem specific to this monitir in that it doesnt like the default 75Hz refreshrates in the 1680x1050 high resolution option, so you have to limit the  refresh5rates to 60Hz

---

### Post by Antexter on 2006-11-03
ahhh help, i can't get on ubuntu now it goes out of frequency how do i put it back (I'm currently using ubuntu live, i also have knoppix live next to me)

---

### Post by stream303 on 2006-11-03
The fastest way I know of to use the open-source drivers and change screen resolution is to find out your video card manufacturer:
```
lspci
```
Then, use the following command (slightly longer than original one found earlier)

```
sudo dpkg-reconfigure -fgnome -phigh xserver-xorg
```

This brings up a nice and simple Gnome dialog box.  Choose manufacturer, then choose desired resolution - ideally your monitor's native resolution

---

### Post by Antexter on 2006-11-03
So how do i fix my linux install?

---

### Post by DCGalen on 2006-11-03
Thanks Kateikyoushi for your suggestion of to configure X again, it has fixed my issue of being stuck at 600x480.  Thanks for the suggestion!

---

### Post by Antexter on 2006-11-03
k i tried 
```
sudo dpkg-reconfigure -fgnome -phigh xserver-xorg
``` 
set it to a high res rebooted and it wouldnt show anything, i think my crt monitor frequensy can only go up to 31khz so any ideas?

---

