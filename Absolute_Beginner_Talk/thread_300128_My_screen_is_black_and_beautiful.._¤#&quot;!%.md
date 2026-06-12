---
title: "My screen is black and beautiful.. ¤#&quot;!%"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by SunshineSmile on 2006-11-15
Hi guys. 

My screen turns black, and displays "input out of range" when I attempt to start my newly installed xubuntu. The live CD worked just fine, but I had to adjust the vga settings when starting the CD to 800*600. 

How do I adjust this before booting now that I have installed xubuntu?

And how come I have these problems now, when previous installations of ubuntu worked just fine? (breezy) ](*,)

---

### Post by junglepeanut on 2006-11-15
What video card do you have? Have you tried to reconfigure xserver yet?

---

### Post by bodhi.zazen on 2006-11-15
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

OR, if that fails to edit xorg.config:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf
```

---

### Post by SunshineSmile on 2006-11-15
I have SiS 650. Reconfiguring xserver tells me little. Do I have to do anything command-line based? Ubuntu breezy worked straight outta the box..

---

### Post by junglepeanut on 2006-11-15
Did you run bodhi.zazen's first command? That will reconfigure as long as you choose the most likely answers.

If not we can look at your xorg.conf as he posted as well.

---

### Post by jd65pl on 2006-11-15
Boot in recovery mode then do:

```
dpkg-reconfigure xserver-xorg
```

Ensure that your driver is "vesa" and the correct resolutions are selected and all other options are appropriate for your system.

---

### Post by SunshineSmile on 2006-11-15
Well, I have no idea what all those options were (BusID of video XKB, keyboard-setups, etc) but I got in!! Now I type from my new xubuntu OS! As an ultra-n00b. Yay!!:KS

---

