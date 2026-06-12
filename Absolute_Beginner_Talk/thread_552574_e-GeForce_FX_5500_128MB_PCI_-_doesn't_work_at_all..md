---
title: "e-GeForce FX 5500 128MB PCI - doesn't work at all."
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by speechtactics on 2007-09-16
lurking a few months... first time poster. i LOVE ubuntu. 

i've spent the better part of the last 3 days on this, and i've concluded that it's just impossible to make it work. I'm playing with a compaq pc... 2.8ghz Celeron D, 1.5gb DDR... a decent machine, with crappy onboard graphics support, and only PCI expansion slots. the best nvidia PCI (not PCIe) cards i could find at fry's were both 5 series-- 5200FX and 5500FX. looking at the forums, it seemed some people had issues with these cards-- but eventually got them settled. i was not so lucky.

i have scoured these forums for hours and hours over the past 3 days. nvidia's forums, too. i have tried everything. the point of this post is to warn other people with the same problem i'm having to *forget about it*! reading every single post i could find about the 52/5500FX yielded the same results: boot up and _____. well what if it won't boot up? what if it locks up during boot? even in recovery mode? this was my dilemma. 

i found that i could tell the BIOS to use the onboard graphics, while the 5200FX was plugged in, and ubuntu would boot fine. i could even use envy to install proper drivers (or do it manually 3 different ways) and even though "all signs point to yes", still, it would hang during boot.

bottom line: if you plug in an FX5200 or FX5500, try to boot, and find that the ubuntu boot splash screen just freezes when about"3 notches" have become orange, you're having the problem i had. to be more clear, if you boot without the usplash, and you get a boatload of page faults/etc and a full system hald at "loading hardware" during boot, you're having the problem i have, and if you're having this problem, do yourself a favor: give up now. 

finally, as one final ray of hope, i'd like to ask the entire community: does this sound like a problem you've overcome with these cards? if so, post now or forever hold your peace.

thanks everyone for all the awesome feedback on these boards. they've been a tremendous help over the last few months... just not with these video cards in particular.

-tactics.

---

### Post by atlfalcons866 on 2007-09-16
you need the nvida drivers.

do sudo apt-get install nvidia-glx

---

### Post by atlfalcons866 on 2007-09-16
or ENVY
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by w4ett on 2007-09-16
Since the card is "somewhat" working I'd  recommend reconfiguring your xorg.conf:

Boot into recovery mode then,


From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

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

