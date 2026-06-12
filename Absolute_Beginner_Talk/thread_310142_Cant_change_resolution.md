---
title: "Cant change resolution"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Thursdae on 2006-11-30
Hi, I just installed ubuntu and I can't change my resolution from 640x480

My GFX card is a ATI Radeon x700 Pro

I know the resolution should be able to go to 1280x1024 but it wont go anywhere, I included a picture.

[http://img150.imageshack.us/img150/2802/screenshotum5.png](http://img150.imageshack.us/img150/2802/screenshotum5.png)

It has no other option but 640x480 and 60hz

Help please!

Thanks!!

---

### Post by taurus on 2006-11-30
You need to install a driver for your ATI card.  Check out this link; scroll down to the ATI section...

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by Thursdae on 2006-11-30
> **taurus said:**
> You need to install a driver for your ATI card.  Check out this link; scroll down to the ATI section...

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

When i do the command ```
deb http://albertomilone.com/drivers/edgy/nonlegacy/32bit binary/
```

it just says ```
bash: deb: command not found
```

---

### Post by taurus on 2006-11-30
You need to add that to your /etc/apt/sources.list!!!  Look at Step 1 again.

---

### Post by bodhi.zazen on 2006-11-30
taurus:

Thanks for the link.

---

### Post by Thursdae on 2006-11-30
I did that >_<

---

### Post by taurus on 2006-11-30
> **bodhi.zazen said:**
> taurus:

Thanks for the link.
No problem, mate.

---

### Post by taurus on 2006-11-30
> **Thursdae said:**
> I did that >_<
Okay, I guess I need to spell out the whole thing then.  Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/apt/sources.list
```
Scroll to the end of it and add the following line to it.

```

deb http://albertomilone.com/drivers/edgy/nonlegacy/32bit binary/

```
Save it and from a terminal, run

```

wget http://albertomilone.com/drivers/tseliot.asc
gpg --import tseliot.asc
gpg --export --armor albertomilone@alice.it | sudo apt-key add -
sudo aptitude update
sudo aptitude install  xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```
Reboot and see what happens...

---

### Post by xabbott on 2006-11-30
I have an ATI card and had the same problem. Instead of installing a new driver right away I edited the xorg.conf and added proper resolutions. 

Depending on your comfort level you can do this in two ways. Run the following command... 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Or hand edit it with
```
sudo gedit /etc/X11/xorg.conf
```

Wherever you see
*Modes    "640x480"*
```
Modes    **"1280x1024" "1024x768" "800x600"** "640x480"
```

---

### Post by Thursdae on 2006-11-30
@ Tauras...

It actualy did something, when i reboot it still doesnt work

@ Xabbit...

I checked and the resolutions are in there already... =\

IDK what to do D: is there somewhere i can check if the drivers are installed??

---

### Post by CatKiller on 2006-11-30
The problem may well not lie with the graphics card, but how the graphics card reports information about the monitor. You'll need to look up the specifications of your monitor for this step, either in the manual, or on the manufacturer's website. You're looking for the Horizontal and Vertical refresh rate ranges. Then you'll put those values in the "Monitor" section of your xorg.conf, like so:

```
        HorizSync       30-72
        VertRefresh     50-160

``` Don't use my values - they might break your monitor. You'll need to find the values for your monitor.

---

### Post by Thursdae on 2006-11-30
```
HorizSync       30-70
        VertRefresh     50-160
```

Is mine, but i dont see where to put it in in the xorg.config

---

### Post by CatKiller on 2006-11-30
In the Monitor section. This is what mine looks like:

```
Section "Monitor"
        Identifier      "Hansol 730E"
        Option          "DPMS"
        HorizSync       30-72
        VertRefresh     50-160
EndSection

```

---

### Post by Thursdae on 2006-11-30
CatKiller... THANKS SO MUCH! I added it in the file like you had yours and it works perfectly! Thanks! Finally its not big as hell D:

<3

---

### Post by CatKiller on 2006-11-30
No worries. Welcome to the community! :D

---

### Post by atr_hugo on 2007-02-27
Well as a new user with an ATI Radeon card I was experiencing the same issue - WAS that is until I followed the easy steps laid out to fix it. Thanks!! Next time I'm on eBay I'll see if I can't buy you a cheap bean to go with your collection. ; -)

---

