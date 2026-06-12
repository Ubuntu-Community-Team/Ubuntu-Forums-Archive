---
title: "Need help with graphics driver"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by HomeImprovement on 2008-03-06
hi all!

i'm quite new to linux, ubuntu and the mainboard i'm using in the box where i'm trying to get it working.

the mainboard is a VIA EPIA-CN13000G, C7/1300Mhz Mini-ITX with onboard graphics (amongst other onboard stuff).

by default it seems ubuntu (gutsy gibbon 7.10) installs a vesa graphics driver, which means i am unable to use advanced graphics stuff, and just get the most basic (no desktop effects for instance).

first of all, when i am trying to change the driver in the graphical interface it won't accept my changes, and keeps on with the vesa driver. has this got to do with administration right (gksudo/sudo)? if so how do i start the "screens and graphics" interface as gksudo?

secondly, i have downloaded the latest openchrome driver, which is supposed to support all kinds of stuff on my mainboard. however, when i want to install the package, i get a message about a conflicting package (xserver-xorg-video-via) and the installation is aborted.

i have honestly over several days tried and tried every pssible solution i have thought of after searching the net. i'm feeling the solution is close, i just can't find it.

i'm really stuck, and need the help from this community.

1. how can i change the grapchics driver on my via epia mainboard?
2. how can i resolve the package conflicts and install the latest openchrome driver?

thanks so much in advance :)

HomeImprovement

---

### Post by gobbles414 on 2008-03-06
HomeImprovement,

Welcome to Ubuntu Linux. VIA hardware does not function very well in Linux, due mostly to a lack of support from VIA. You really only have three options to get your graphics working with a VIA motherboard in Ubuntu:

1. Install VIA's official driver for your motherboard/chipset using the information found [here]("https://help.ubuntu.com/community/UniChrome").
2. Install the open source drivers for your motherboard/chipset using [this]("https://help.ubuntu.com/community/OpenChrome") procedure.
3. Purchase a Linux-friendly graphics card that will fit in your PC.

Neither option one nor option two were successful for me with my VIA motherboards. I never got around to trying the third option. But at least in theory, a graphics card will solve your graphics-related problems.

---

### Post by HomeImprovement on 2008-03-07
thank you for your quick reply! 

i of course ran home straight after work and tried the solutions you reccomended, but to no awail.

the problem isn't so much as to install the driver, but to get the system to acutually use the driver. first of all i'm not even sure how to change the driver. as far as i have noticed there's nothing different in the driver list in "screens and grapchics" after installation (i tried both suggestion 1 and 2). there don't seem to be any new options for me to use after installation.

and either way - my system won't let me change the driver. by default it uses the vesa generic graphics card driver, i change it i.e. to the s3 driver from the list, press ok and cross my fingers.

after a second of black/blank screen the dialog disappears and the system returns to its former state. when i go back to "screens and graphics" it tells med it's using the vesa generic driver.

i have thought of manually editing xorg.conf but i am not sure what information to add, like the name of the driver etc.

any thought? anyone?

thanks

HomeImprovement

---

### Post by rjmoerland on 2008-03-07
The script in this post might work for you:

[http://ubuntuforums.org/showthread.php?t=485646]("http://ubuntuforums.org/showthread.php?t=485646")

It will install and select the openchrome driver in X. Your milage may vary though. I got the best (stable) results with the stock X.org VIA driver.

---

### Post by skymera on 2008-03-07
my laptop has VIA chipset, and i must say Unichrome works a lot better than openchrome.

but still cant do 3D stuff very well.

---

### Post by gobbles414 on 2008-03-07
> **HomeImprovement said:**
> thank you for your quick reply! 

i of course ran home straight after work and tried the solutions you reccomended, but to no awail.

the problem isn't so much as to install the driver, but to get the system to acutually use the driver. first of all i'm not even sure how to change the driver. as far as i have noticed there's nothing different in the driver list in "screens and grapchics" after installation (i tried both suggestion 1 and 2). there don't seem to be any new options for me to use after installation.

and either way - my system won't let me change the driver. by default it uses the vesa generic graphics card driver, i change it i.e. to the s3 driver from the list, press ok and cross my fingers.

after a second of black/blank screen the dialog disappears and the system returns to its former state. when i go back to "screens and graphics" it tells med it's using the vesa generic driver.

i have thought of manually editing xorg.conf but i am not sure what information to add, like the name of the driver etc.

any thought? anyone?

thanks

HomeImprovement

Hi... I believe that installing the *xserver-xorg-video-openchrome* package automatically uninstalls the other VIA-related graphics packages. Try typing *chrome* into Synaptic to see which VIA-related packages are currently installed. Obviously, be sure to uninstall the official VIA driver and reboot before making another attempt to install the open source driver. By the way, both the instructions for the open source driver and the readme for VIA's official driver (I think) mention what you need to edit in your xorg.conf.

Like I said in my original reply, you're probably just wasting your time trying to get your VIA integrated graphics to work in Ubuntu. Your best bet is to skip to the third option -- a new graphics card. That's just my humble opinion...

---

