---
title: "ASUS X53S - things that won't work"
date: 2011-06-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by elodsson on 2011-06-15
Hi there!

I just bought a new ASUS X53SV laptop with Windows 7 on it. But ever since i have my own computer, i have a dual boot system with Ubuntu, so why change it this time. I decided to go for the 64 bit. After installing my favorite stuff i tried to simply enjoy it. These are the things, that are still giving me a headache:

1. The Nvidia Geforce GT 540M video driver is not working. I have crummy image, things like Compiz, TORCS etc. won't run, AWN looks like stone age.
I have downloaded the [proper Nvidia driver]("http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html") from Nvidia homepage, and tried to run it as root, but i got the following message: [COLOR="DarkRed"]ERROR: You appear to be running an X server; please exit X before installing. For further details please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).[/COLOR]
I tried to google it, but no luck.

2. Some functions of the Fn key are not working. Till now it only reacted to the brightness buttons, the SRT/VGA switcher, and the Insert button. But i cannot set the sound for example, or switch the touch pad on or off.

Well, that's it for now. If anyone could help me with these, i would be really grateful.

---

### Post by cucisan on 2011-06-25
hello there,

i got myself a A53SV yesterday... which is the same as the K53SV (i5, gt540m, ...)

for nvidia to work you'll need bumblebee which is something similar to "nvidia optimus"... 

it worked for me to use intel/nvidia simultaniously but when i install it, my fan starts to go mad and run fullspeed all the time.. no fix yet.. though yours might work :)

---

### Post by cucisan on 2011-06-26
i tried to do a howto on how to get these things working you described

take a look here :)

[http://ubuntuforums.org/showthread.php?t=1791081]("http://ubuntuforums.org/showthread.php?t=1791081")

---

### Post by Sylslay on 2011-06-26
Is more likely that he will get same issu wtih fun.

Same laptop+ same mobo =same sensors.

Why nvidia does't suppot opitmus for linux?

Not fair.:confused:

---

### Post by cucisan on 2011-06-30
> **Sylslay said:**
> Is more likely that he will get same issu wtih fun.

Same laptop+ same mobo =same sensors.

Why nvidia does't suppot opitmus for linux?

Not fair.:confused:

well there seem to be some differences.. i didnt find many k53sv users who have fan problems.. but i already found a cure for it, as well as touchpad multitouch, and also for the fn keys... all posted in my thread. hope it helps

---

### Post by Mindrage on 2011-09-07
I can also say that bluetooth doesnt work, as i have it functional in my Windows 7, but not in my Kubuntu 11.04

---

### Post by Ender516 on 2011-11-15
HI, I also own a Asus X53S, with nvidia gt540M. 

With Ironhide I can manage the application that requires the card but I'd like to get an higher resolution of my screen. Actually I've 1366x768, but if I run nvidia-settings under Ironhide I read 1920x1080!

Somebody knows how to set it?

---

### Post by johnc@crosslink.net on 2011-11-17
I just got a deal on an i7 x53s from Microcenter. Install of 11.10 is so far pretty stable: both hib & suspend work without issue, for instance. May need to custom kern for control of the processors (battery at 2hrs), and some key copying for he f keys, but this seems stable.

---

### Post by thumaszz on 2011-11-18
I got the exact same problem as you, I have a Asus K53SV with an nVidia GT540M.
And when I try installing the nVidia Driver I get the server error, and when I use another driver unity just doesn't start and all the other openGL software. But Ubuntu thinks I have a GT555M, you can check it with "lspci -v | grep -i vga" in Terminal, I get this:
     > 
                                                 00:02.0 VGA compatible  controller: Intel Corporation 2nd Generation  Core Processor Family  Integrated Graphics Controller (rev 09) (prog-if  00 [VGA controller])
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT  555M] (rev a1) (prog-if 00 [VGA controller])                                  
It thinks I have an nVidia GeForce GT 555M, but I have a nVidia GeForce GT 540M.

---

### Post by lorebett on 2011-12-04
any update about ubuntu on this ASUS X53S series?

---

### Post by tillie on 2011-12-06
I got this laptop as well. 

Please, people at least answer with something (like "ergerwstryjtye") to let us know that at least you saw our problem! Not saying anything is rude.

---

### Post by Lekensteyn on 2011-12-21
> **Ender516 said:**
> HI, I also own a Asus X53S, with nvidia gt540M. 

With Ironhide I can manage the application that requires the card but I'd like to get an higher resolution of my screen. Actually I've 1366x768, but if I run nvidia-settings under Ironhide I read 1920x1080!

Somebody knows how to set it?
The resolution visible under ironhide is not usable. It's written in a configuration file just in case someone happens to use a monitor that supports this resolution.

---

