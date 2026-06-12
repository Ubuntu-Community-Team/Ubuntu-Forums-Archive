---
title: "how do i install drivers"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by daz87uk on 2007-01-09
im new to ubuntu, and just made a duel boot with windows xp pro, im having problems with sound and video driver and i dont have a clue how to get them. i have a fairly new machine i built from parts. i have a Saphire Ati crossfire express 3200 (PC-A9RD58OAdv) motherboard and ATI Radeon X1900 XT 512 graphics with AMD's 3200 duelcore and Crucial Ballistix 2GB Ram. now i know none of the driver are compatible with windows the ati graphics drivers conflict with HD Audio built on the Motherboard and i had to use omega drivers to get both to work. but coming into this new operating system which works completely different i dont have a clue lol. so any help would be most appreciated.
I need;
[LIST]
[*]HD Audio Drivers
[*]ATI X1900 XT Graphics Drivers
[/LIST]
I also dont have a clue about installing things i found ATI's graphics drivers downloaded them but they dont work. it just says; gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again. the extension is .run
](*,)

---

### Post by dorcssa on 2007-01-09
Try these for the ATI driver. Here is for dapper(6.06): [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
and for edgy(6.10):[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) Of course gedit tells you that, you are trying to open a deb package, a binary file(it's like an exe on windows), with a text editor..

---

### Post by raul_ on 2007-01-09
[ATI Drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

[How to install anything in Ubuntu]("http://ablog.apress.com/?p=1062")
About the audio drivers, once you get the hang of it from the 2 links above, try to install ALSA drivers. I think they support pretty much every sound card :rolleyes:

---

### Post by daz87uk on 2007-01-09
Thanks i will give this a try :-D

---

### Post by Ben Sprinkle on 2007-01-09
```
sudo dpkg-reconfigure xserver-xorg
```
When you get to the video driver screen select ATI or fglrx for default or find your previous driver. Then reboot.

---

### Post by daz87uk on 2007-01-09
how do i find the bus identifier of the graphics card i am trying the method; sudo dpkg-reconfigure xserver-xorg

---

### Post by Ben Sprinkle on 2007-01-09
```

sudo lspci

```
I think, or just look at it here:
```

sudo gedit /etc/x11/xorg.conf

```
My laptop is PCI 0:2:0 or something, I think most are 1 instead.

---

### Post by raul_ on 2007-01-09
That's all in the guide i posted, so follow it instead, before you are comfortable with other methods

---

### Post by daz87uk on 2007-01-09
thank you all i will try those methods as well as the help documents :-D

---

