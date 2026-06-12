---
title: "Can't change screen resolution"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by bharkins on 2008-01-02
I am a total noobie and this is my first post. I installed nvidia-glx-new to get the desktop effects using compiz. However, in restarting, the screen resolution comes up  in highest format and there is no option to change it back to my normal 1250X786. I have not installed compiz yet. Any suggestions?

---

### Post by CameronCalver on 2008-01-02
so you havent tryed in system screens and monitors? or try reconfiguring x

---

### Post by bhold on 2008-01-02
This has happened to me a few times - cause was missing information in /etc/X11/xorg.conf. Last time it happened was when I upgraded from Ubuntu 7.04 to 7.10.

The cause on my system was missing HorizSync and VertRefresh lines. These go in the "Monitor" section. I added the lines manually then re-started X to fix the problem. On my system, the Monitor section of xorg.conf is as follows, although you will need the specs for your own monitor to set the appropriate values:

Section "Monitor"
        HorizSync       30-80
        Identifier      "DELL E177FP"
        Option          "DPMS"
        VertRefresh     43-75
EndSection

If you don't want to mess around modifying xorg.conf you can try reconfiguring it automatically with the following command:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by matchstich on 2008-01-02
i went from 7.04 to 7.10 and the first time i changed my resolution , it held

but now it went to the highest, and i can not change it. found this thread.

i tried what bhold suggested and got this

sudo dpkg-reconfigure -phigh xserver-xorg

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080102200034

and i still can not change the resolution

thanks

---

### Post by jken146 on 2008-01-02
Do it without the -phigh.  You'll have to go through the wizard but you will be able to pick your desired res.

---

### Post by chronic on 2008-01-02
install nvidia-setting i think its called, type nvidia into synamptic 

aned change the res with that

---

### Post by bharkins on 2008-01-03
I have an old Dell laptop (Inspiron 8200) with XP/Gutsy/Feisty installed - no apps running. On Feisty, 
I tried the sudo reconfigure command, but after many screen asking for input, received following error: Microcode "blm43xx-microcode5.fw" not available or load failed. Any suggestions? I may reinstall Feisty and try again.

[Just for FYI, I am on several forums, Windows based, and this one is by far the most active I have seen. Great for noobies like me]

---

### Post by matchstich on 2008-01-03
> **jken146 said:**
> Do it without the -phigh.  You'll have to go through the wizard but you will be able to pick your desired res.


i tried this.  don't know what i did, but i can not start the machine.  it is telling me i have a lot of errors

in the x.org folder and that i need to fix them.  only thing there is a command prompt.

did not know what to do. so, i reinstalled the OS.  that system has a inboard and a g-force 4000.

never could finger out to disable the inboard.


not sure what i did when i had 7.04  but, it worked right.  

gonna have to wait for the weekend when i have time to get back to it. i have a few back up machines to


use in the meantime.

thanks

---

### Post by matchstich on 2008-01-05
> **chronic said:**
> install nvidia-setting i think its called, type nvidia into synamptic 

aned change the res with that


 installed this, but where is it hiding?  can not seem to find it.
thanks

---

### Post by bharkins on 2008-01-06
> **matchstich said:**
> installed this, but where is it hiding?  can not seem to find it.
thanks

OK, I also installed nvidia-settings and it was "installed". I too, would like to know where it is as the description seems like a useful tool. I'd like to know as a total n00b, how does one locate any downloaded/installed software via Synaptics?

---

### Post by bharkins on 2008-01-06
> **bharkins said:**
> OK, I also installed nvidia-settings and it was "installed". I too, would like to know where it is as the description seems like a useful tool. I'd like to know as a total n00b, how does one locate any downloaded/installed software via Synaptics?

OK, I used the command "whereis" for nvidia-settings which lead to /usr/bin/nvidia-settings, but it is quite useless as far as setting up screen resolution. There's got to be an easier way as this gets done in Vista a a couple of seconds in a GUI window. I'm not sure nvidia-settings sets any screen resolution settings, unless someone can point me in the right direction.

---

### Post by phidia on 2008-01-06
barkins, goto System>Administration>Restricted Drivers Manager 
You should be able to enable the nvidia propritary driver from there.

---

### Post by bharkins on 2008-01-07
> **phidia said:**
> barkins, goto System>Administration>Restricted Drivers Manager 
You should be able to enable the nvidia propritary driver from there.

Yes, I have tried that - the restricted driver is nvidia-glx-new which only allows one resolution size, the highest 1680X1050. Thus, still can't change screen resolution.

---

