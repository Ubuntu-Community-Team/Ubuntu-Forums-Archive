---
title: "a few problems with ubuntu"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by chronic on 2007-05-17
hello everyone

This is my first post but i thought I would quickly introduce myself.

I'm very new to Linux but iv been using computers for years. I never tried linux but a friend recommended ubuntu a couple weeks ago. Since then i haven't used windows once and i don't miss it. Obviously there is still can't do but I'm getting there.

i hope i can make the switch to Linux once and for all. :lolflag: 

Anyway this is just a couple of quick questions. 

Im using ubuntu i386 32bit feisty fawn and i have beryl installed but i dont use it all the time. im not 100% sure what i did with the drivers but the tutorial i used is here - [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

i have an ATI Radeon x800gt all-in-wonder gfx card

if you need any more info then just ask as im not sure what you need.

my first problem is that i cant seem to get any videos to work properly. they either crash  after a few minuets (completely crashes Ubuntu) or i get a black screen on the player. very occasionally they do work ok though 

My second question is. Is their a way to set the resolution higher than 1024x768. My TFT has a native resolution of 1280x1024 so when i run it at anything lower the screen looks very blurred. 

also i would like some help with wine. Can someone give me a very quick tutorial or give me a link to one. I cant get it to do anything but i would like to install MS office and photoshop if thats possible.

can you please explain everything in very simple terms as i am still a newbie :lolflag:

Thanks
Any help is appreciated

---

### Post by Happy_Man on 2007-05-17
yes there is a way to fix your resolution: run the command ```
sudo dpkg-reconfigure xserver-xorg
``` from a terminal, and answer all the questions. When you get to the part about what screen resolutions you have, scroll and select 1280*1024. 

Why do you need MS Office? OpenOffice does everything MS Office does, plus a couple more things. Photoshop 7, I believe, is the maximum WINE can handle, so if you need CS3 you're out of luck. 

There is a great WINE howto somewhere on the forums here... i'll let you know if I find it.

---

### Post by blazercist on 2007-05-17
ok these things are probably happening because you dont have the drivers installed correctly.

You have an ATI card correct?

Type fglrxinfo into console and paste the results here.

---

### Post by testube_babies on 2007-05-17
For MS Office (up to version 2003) or Photoshop (up to version 7), I recommend Crossover Office:
[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

However, if you're like most of us you'll find that OpenOffice and the GIMP are apt replacements and do just about everything you'll ever need.

---

### Post by derred on 2007-05-17
I recommend using Automatix to install wine for you (as well as a bunch of other stuff). I recommend using GIMP or GIMPshop instead of Photoshop and Openoffice or GnomeOffice(Abiword, Gnumeric and so on) in stead of M$ Office if you don't need very specific things in them. If you have to have the latest MS Office or Photoshop I recommend you look into virtualization (running Windows in a window as is were on top of Ubuntu) and Automatix gas a couple of virtual machines in it's list.

[http://www.getautomatix.com/](http://www.getautomatix.com/) is a great resource for beginners.

Best of luck!

---

### Post by chronic on 2007-05-17
thanks for the speedy responses

> **Happy_Man said:**
> yes there is a way to fix your resolution: run the command ```
sudo dpkg-reconfigure xserver-xorg
``` from a terminal, and answer all the questions. When you get to the 

this didn't work i still have only 1024x768 res. im sure its something that iv done but it hasn't worked.

when i tried

 ```
fglrxinfo
``` it gave me this 

```
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
Make sure you have the 'restricted' component enabled
bash: fglrxinfo: command not found
```

---

### Post by chronic on 2007-05-17
i already have automatix installed and i have to say its great. it saved me a lot of time and work.

i have also installed wine through automatix but i havent been able to do anything with it yet.

---

