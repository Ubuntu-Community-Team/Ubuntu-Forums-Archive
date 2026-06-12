---
title: "X server problems"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by Namingishard on 2006-07-23
When i pop in the live CD(Ubuntu), it starts to load all of whatever it is its loading, when it gets about 5mins in i get a message saying something like "X server not configured right" and then the screen goes all waky and there is text every where and i can't read most of it.
I know pretty much nothing about Linux so i have no idea what could be wrong >_<.

---

### Post by adam.tropics on 2006-07-23
do you know what video card you have?

---

### Post by Namingishard on 2006-07-23
Yes, Its Radeon 9100(no laughing)

---

### Post by adam.tropics on 2006-07-23
so you need to first get into x, then grab the fglrx drivers. So in the mean time, just to get you into a graphical environment, when you see all that blue garbled mess, hit enter twice, and you will be at a command prompt.

type

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the thing through selecting the vesa driver, and then after that

```
startx
```

and you should be in gnome. Then post again for part2 !

---

### Post by tseliot on 2006-07-23
Try booting the CD in Safe Mode

---

### Post by Namingishard on 2006-07-23
Ok i did all that what you said and when i type in startx i get awhole screen of error, i wrote down what i thought might be importent.
So here it is
(WW)Vesa:nomutchin device section for instance (busID PCI:1:10:0) found
(EE)Vesa(0): cannotreadC-BIOS
Fatal Server error
No screens Found.

---

### Post by adam.tropics on 2006-07-23
well if vesa won't run, which is pretty odd, as reccomended by Mr Eliot, is safe mode is no good either?

---

### Post by Namingishard on 2006-07-23
Got same errors when i ran in Safe mode

---

### Post by Android565 on 2006-07-23
I'm having a similar problem (i have now installed ubuntu via the text installer), im running an X800XL and ive tried several setups (inc ATI, vesa and fglrx drivers and low resolutions) but X server will still not start, although i have only tried to start it using the command "/etc/init.d/gdm restart", is "startx" likely to work any better or is there something else i could try? Safe mode just puts me into the command line same as a normal boot

Just thought i would add the error i get is slightly different, it says something like "starting GNOME Display Manager [COLOR="Red"][fail][/COLOR]"

---

### Post by Namingishard on 2006-07-23
Sooo, All hope lost?

---

### Post by Namingishard on 2006-07-23
Ok, i relize that prolly noone has a fix or an anwser but the problem is my video card yeah? if i upgrade will that work? possibly?

---

### Post by arkangel on 2006-07-23
it seems  that your xorg.conf   is not  pointing to the right PCI  Bay 

go to the bios and try to find out in which  bay is the  card ,

for example  mine is  in PCI:3:0:0 instead of PCI:1:0:0

---

### Post by Namingishard on 2006-07-23
Ok, ill try that! but how exactly would i go about it doing it?

---

### Post by arkangel on 2006-07-23
try to get a console 

then as su  edit the /etc/X11/xorg.conf

look for a line  that says (in the Section "Device")

BusID       "PCI:1:0:0"
and comment it,then  

#startx

---

### Post by Namingishard on 2006-07-23
hmm...ok

---

### Post by Namingishard on 2006-07-25
So how do i figure out where to point it to?

---

### Post by arkangel on 2006-07-27
type lspci  in the console  and look for a description of your card  it will tell you in which bay is connected

---

