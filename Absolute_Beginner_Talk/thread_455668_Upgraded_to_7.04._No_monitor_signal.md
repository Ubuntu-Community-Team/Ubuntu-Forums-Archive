---
title: "Upgraded to 7.04. No monitor signal"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by BriDude on 2007-05-26
Hey all,

Specs:
AMD Athlon 64 processor 3500+
ATI Radeon X800+ (PCI)
2.2GHz
1024 RAM 

I upgraded to kernal 2.6.20-15 from 2.6.17-11 last night and now I can't even make into the login screen. 
(2.6.15-27-amd-64 still works). After hitting the power on my computer I'm able to select my OS (Ubuntu or XP) and the various Kernel versions. When I select 2.6.20-15-generic the screen fills with white letters (Nothing strange) 
then  says "Kernel Alive" and some numbers. Then my monitor loses its signal and the Caps, Num, and Scroll LEDS on my keyboard begin to blink. 

I read through the ATi X**** video card sticky but since I'm just trying to update my distribution I'm not sure if that applies. I did try booting up kernel 2.6.20-15 recovery and entered:

sudo apt-get update
sudo apt-get dist-upgrade

udo apt-get install xorg-driver-fglrx

sudo depmod -a

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
(*Code from the sticky)

That didn't work unfortunately. 

I also experimented with the Live CD.
When I booted with the CD Startup made it to the Ubuntu loading bar (Further than the HDD boot) but after a short while the screen went blank (the signal wasn't lost and no Keyboard LEDs) 

When I tried booting from the CD in Safe Graphics Mode Ubuntu loaded properly.  

I'm pretty new to all things Linux so I hope you'll bare with me. 
Thanks in advance ;)

---

### Post by arijarot on 2007-05-27
maybe you can try ```
dpkg-reconfigure xserver-xorg

``` ? then restart x...

---

### Post by BriDude on 2007-05-27
Thanks arijarot. I appreciate the help but unfortunately I tried that already and no go. 

I've been playing around and I can get to the desktop through recovery mode and *startx*. I also followed this guide to install the drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

The fgkrx seems to be loaded correctly but my problem still persists.

---

### Post by Pizzarth on 2007-05-27
I don't think the drivers are the problem. I think that the x-server was set to the wrong resolution. some monitors, instead of compensating, just give a no signal error, or an out of bounds error when the wrong resolution is given. look if there's a resolution that shouldn't be there under the xorg.conf file in /etc/X11/

well that's just what happened to me, and I guess might be happening to you.

---

### Post by mattegeniet on 2007-06-01
Hi! I'm having the exact same problem. When trying to boot There is some text about loading the kernel and suddenly i get a no signal error. 

It was the same thing when I tried to boot from the live cd, but i managed to get around this by specifying that "1280*1024 32bit" was the resolution to be used. When I got into the OS then all graphics were very "pixly" and text was hard to read.

I installed everything and when I tried to boot again, exactly same problem occured. I tried booting in recovery mode and that works fine, and I then installed fglrx and reconfigured xorg. Then I can start x with startx and everything works perfectly. But I still can't boot directly from GRUB. 

So it can't be anything with xorg, because it works fine when started with startx, it has to be with the booting screen, because changing resolution here helped me out in the installation. But how to change resolution for the startup screen? My experience of linux isn't very big either, but at least I have some...

---

### Post by mattegeniet on 2007-06-01
Hello everybody! Now I thinknk I've found at least a part of the solution. By editing */boot/grub/menu.lst* and adding a screen resolution (in my case 1280*1024 (VGA=794)) i got the splash screen at start. For information on how to this check out this: *[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)* You find it in the last section at point 6.  Unfortunatly, when the loading is done, I still get an "no signal"-error, without any login screen. 

How about everybody else?

I think it's be a bug somewhere in the startup script, because it works fine until the login screen, and - as mentioned before - it works starting in recovery mode and startx, making it unlikely that there's anything wrong with  the x configuration. But since I've got very poor programming skills and knowledge in linux, i've got no idea what kind of bug it could be...

I'm running kernel version 2.6.20-16, radeon x800XT using fglrx and a lcd screen from BenQ by the way (if anyone would wonder).

---

### Post by mattegeniet on 2007-06-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/86666](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/86666) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This problem seems to be very closely related to bug [#86666]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/86666")

---

### Post by Nekomusume on 2007-06-02
I've got a similar problem - I tried to boot up a liveCD in order to try ubuntu out, and got a 'no signal' problem after the loading screen. It made the startup noise, so it seems the OS was running.

AMD 2200, 2GB Ram, GeForce 6800GS

It worked fine on another PC i've got access to, but I can't really do that much with it on that system.

---

