---
title: "SLI woes"
date: 2009-07-26
forum: Apple Hardware Users
---

### Post by Kver on 2009-07-26
*Solved, see next post if you're in a similar situation*

I've installed Kubuntu on a brand-new mac pro. It's a completly stock system on exception of the video-cards: I am using a second nvidia G120 in an SLI configuration. I need it for 3D modelling in OSX, so I cannot take it out. Ideally, I won't want to buy a new video card expressly because Ubuntu doesn't play nice with SLI.

On a vanilla install, I get the usual tiny resolution expected of the vesa drivers; However switching to nvidia drivers it fails to boot into the GUI:

"No screens found"

I've tinkered for several days now, here's the steps I've taken:

I've ran the commands...
nvidia-xconfig --only-one-x-screen --sli=auto
nvidia-xconfig --sli=auto
nvidia-xconfig --only-one-x-screen --sli=auto -a
(and several other combinations)

after failing at every one of those, I did it all again, on exception of manually editing xorg and setting BusID to either "PCI:2:0:0" or "3:0:0"

nvidia-settings fails, and tells me I have no displays.

Aly help would be deeply appreciated.

---

### Post by Kver on 2009-07-26
After much work, I've figured out what you need to do. This is after you install the drivers through the GUI, and are forced into command-line.

1. Get into command line
[COLOR="DimGray"]You should probably ignore this walkthough if you werent forced into it[/COLOR]

2. enter "lspci | grep VGA"
[COLOR="DimGray"]This will output your video cards, and their Bus IDs. Guess which card has your monitor plugged into it, and jot down the Bus ID[/COLOR]

3. Enter "sudo nvidia-xconfig"
[COLOR="DimGray"]This will have Nvidia set up your graphics card. I reccomend trying to see if this works before continuing.[/COLOR]

4. Enter "sudo nano /etc/X11/xorg.conf"
[COLOR="DimGray"]In the "device" section, add the following lines:
BusID "{enter in the BusID from #2}"
Option "SLI" #Because you have more than 1 card
Option "NoLogo" "True" #To avoid having an Nvidia logo popup[/COLOR]

5. If you get a black screen when you restart, go into safe mode, enter the root terminal (near the bottom of th list) and repeat 2-4 until you guess the correct BusID

6. If it still doesn't work, it is beyond the scope of my abilities.

---

