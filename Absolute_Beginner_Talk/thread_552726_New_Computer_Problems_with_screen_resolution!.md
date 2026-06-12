---
title: "New Computer/ Problems with screen resolution!"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Chamelion on 2007-09-16
I just bought a new computer. Intel Core 2 Duo. 512 Mb  Nvidia GF 8500GT PCI-E Graphics card.
I am running Feisty on my old computer. I just tried the Gutsy Tribe 5 CD 64 Bit (Live) and the Feisty 64 Bit.
The monitor (Asus 1680 x 1050 resolution) turns itself of when loading. When I turn it back on I can get into Ubuntu. My problem is that the highest resolution I can get is 1024 x 768. This is on the live CD. Is there any way I can avoid this when I install? 
Does the alternate install CD give me options to set the screen resolution?
Or after installation could i use a program like ENVY to install the Nvidia drivers and then set the resolution in the Nvidia control panel?
I am still new to this and am very bad with the command line.
Ubuntu has been my main OS for almost 7 months now and I really could not miss it.
(I am dual booting XP with Sabayon on another hard drive. I absolutely hate XP and only use it for the very, very few things I cannot do on Linux.)  Sabayon is very cool, but I am not savvy enough to install more things into Gentoo. ( Or uninstall)  
I have been using Ubuntu for all the series work. 
If you detect a certain amount of panic here, you are right. 
Sorry for going on like that.:lolflag:

---

### Post by w4ett on 2007-09-16
Go ahead and install from the Live CD...the diver 'nv' will load then:

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by Chamelion on 2007-09-17
Thanks for the advice. I am running into a few problems with the 64 edition though.
On launching the monitor turned of again. Last message I could see was:
Kernel direct mapping tables up to 1000000 @ 8000. Went very quick so numbers might not be exactly right.
Then the monitor was of again. The computer kept on running. After a minute I turned monitor back on and Ubuntu was there. Even the right resolution. (This is with Gutsy) Monitor also turns of with Feisty 64 though.
I installed anyway. After instatallation took out the live CD and rebooted. Same situation. Monitor went blank. After I turned the monitor back on I was straight at the Ubuntu log in screen. There was no chance to access my other operating systems anymore, regardless from which hard drive I was booting. 
I have fixed that by now (Super Grub Disc). 
But now Ubuntu on the other drive has become unbootable. I already have Sabayon 64 bit installed so I think there is no problem with the format and the computer.
I tested the 32 bit Feisty disc and it works (live). So I will have Ubuntu eventually, but I would very much like to use the 64 Bit.
Would anybody please have some advice?:(
Thank you again

---

