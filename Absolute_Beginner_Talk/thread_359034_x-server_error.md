---
title: "x-server error"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by dracomordag on 2007-02-11
hey, i'm trying to switch to Ubuntu, and when booting from the LiveCD, i get the following series of errors:

[IMG]http://i58.photobucket.com/albums/g245/dracomordag/DSCF0044.jpg[/IMG]
[IMG]http://i58.photobucket.com/albums/g245/dracomordag/DSCF0045.jpg[/IMG]
[IMG]http://i58.photobucket.com/albums/g245/dracomordag/DSCF0047.jpg[/IMG]




i've looked around and figured out that it's most likely because i have an ATI graphics card, but i can't figure out how to get the "fglrx" thing working. any ideas?

---

### Post by shareMenaPeace on 2007-02-11
Maybe you can just reconfigure the xserver
```
sudo dpkg-reconfigure xserver-xorg
```

What are your system specs? Ram?
 
Maybe try the alternate LIVE CD release.

---

### Post by dracomordag on 2007-02-11
2.7 Ghz
512 RAM
Radeon 9200 PRO graphics card



i've found some documentation on this site about ways i can help this, but so far every one of them assumes i can use the computer in question. i need to be able to do this entirely from the boot screen, which currently isnt even giving me a command line prompt.

---

### Post by nickoli_02 on 2007-02-11
run this from the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

Then when you get to the option to select which video driver to use, select "vesa", NOT "ati". The graphics rendering for vesa is crap, but it'll work and you can then install the fglrx driver :)

Oh for the rest of the options, set it up as you see fit. It's pretty straightforward.

---

### Post by dracomordag on 2007-02-11
i have no terminal

---

### Post by nickoli_02 on 2007-02-11
Sorry, I just read the part where you said you can't get to the terminal. Is there a recovery mode option with the live CD? To be honest I've never used it, sorry. If/when you get around to installing ubuntu you'll need to do as I outlined above.

If I remember correctly, if you select "No" when you get that blue screen it sends you to a terminal...

---

### Post by dracomordag on 2007-02-11
yea, i somehow got a terminal one of the 50 or so times i tried it, but i cannot repeat whatever i did to get there.

---

### Post by dracomordag on 2007-02-11
alright, i got a terminal this time, and typed in the code as you said

i (perhaps stupidly) basically just said "okay" through the immense multitude of options that came up, making sure to choose vesa instead of ATI. (there were about 30 other options, anything i should know about them?)


anyway, how i'm back at a command prompt. do i just reboot?

---

### Post by shareMenaPeace on 2007-02-11
shutdown/restart with
```

sudo shutdown -r now
```

---

### Post by dracomordag on 2007-02-11
i hardware rebooted (aka held down the power button) because it said i needed to be root to reboot


now the error still pops up and i have no terminal

---

### Post by shareMenaPeace on 2007-02-11
When you boot you see the GRUB boot loader start the recovery moide and try it again.

---

### Post by dracomordag on 2007-02-11
what?

---

### Post by bulldog on 2007-02-11
> **dracomordag said:**
> i hardware rebooted (aka held down the power button) because it said i needed to be root to reboot


now the error still pops up and i have no terminal

If you see the X-server message just click it away.
Hit CTRL-ALT-F1 to get to a console and ```
sudo dpkg-reconfigure phigh xserver-xorg
```
Don't reboot just type ```
startx
``` and see if this will work.

---

### Post by nickoli_02 on 2007-02-11
ohh sorry I keep leaving out little details, haha. Since you're using the LiveCD your settings are probably not getting saved (makes sense). After you reconfigure xserver like I instructed above and you return to the terminal, type 

```
startx
```

This will start the xserver, and you should be up and running with a GUI. You'll most likely be stuck with a crappy resolution, and crappy rendering, until you get fglrx running...

The other options in dpkg-reconfigure are for setting up things like your keyboard layout, mouse, display, etc. It's good to read each step to see what you're saying "OK" to, but normally you'll be saying OK anyway.

---

### Post by dracomordag on 2007-02-11
i hate to be more of a bother, but would you guys mind helping me figure out how to get this fglrx running? would i first need to actually install Ubuntu instead of just running it from the LiveCD?


oh, and yea... i got it working. thanks a lot, guys.

---

### Post by shareMenaPeace on 2007-02-11
Yes install ubuntu and if yu cant boot the LIVE CD try the alternate release.

---

### Post by nickoli_02 on 2007-02-11
Don't worry no one here minds helping out someone who's serious about giving Ubuntu a shot. If you want fglrx installed I'm pretty sure you're going to need to install Ubuntu on your computer so you can actually install other apps and such. I prefer the Alternate install CD, it seemed to be faster and I didn't have to deal with actually getting the xserver running until after I installed. 

Once you have Ubuntu installed, and xserver running with vesa, try this howto to install fglrx:

[fglrx in edgy]("http://www.ubuntuforums.org/showthread.php?t=291464&highlight=edgy+fglrx")

The first part of the howto is to set up fglrx in Edgy Eft, the second is to install some additional eye candy.

---

### Post by dracomordag on 2007-02-11
david@desktop:~$ sudo cp /lib/modules/`uname -r`/volatile/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko
cp: cannot create regular file `/lib/modules/2.6.17-11-generic/misc/fglrx.ko': No such file or directory



what in da hell?

---

### Post by nickoli_02 on 2007-02-12
That means the file you're trying to copy doesn't exist... I don't understand why you're doing that :)

---

### Post by dracomordag on 2007-02-13
eh, it was just something about backing up things



now im just confused as to why beryl wont even come close to working

---

### Post by dracomordag on 2007-02-13
i just started getting these errors again

---

### Post by dracomordag on 2007-02-13
alright, fixed it.

---

