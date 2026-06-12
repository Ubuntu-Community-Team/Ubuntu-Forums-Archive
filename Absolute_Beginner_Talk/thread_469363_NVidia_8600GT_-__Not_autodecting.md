---
title: "NVidia 8600GT -  Not autodecting"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by savage.stoo on 2007-06-09
Hi 
First Linux install, so please type slowly and clearly ;)

Installed Ubuntu from a Linux magazine disk, and found that the screen resolution only went as far as 1064x768 @60Hz
I know that  both my Graphics Card, (Nvidia8600GT) and monitor can both handle higher res.

Any ideas anyone?

Currently running
AMD x64 5600+, 2gb ddr2, with a 40gb raptor

All help appreciated.

---

### Post by starcraft.man on 2007-06-09
Magazine disk? They are giving Ubuntu away with magazines? Where is this?

Ok well. First a few things to do to get this working. It's good that you have an NVidia card, they are well supported.

Step 1: Download and run Envy to install drivers. Go to this[ site here, ]("http://albertomilone.com/nvidia_scripts1.html") and download the latest _stable_ release, you want the deb file. Then double click and install it on your desktop. Once its installed in your computer, go to Applications > System Tools > Envy. Click on automatically install NVidia drivers and off you go. Answer yes to any prompts, either in the terminal or in a dialog. When you reboot you will have the drivers installed.

Step 2: Reconfigure xorg to ensure detection. To make sure your monitor is detecting right screen and that the driver is right we will run following command in the terminal (Applications > Accessories > terminal):

```
sudo dpkg-reconfigure xserver-xorg
```

Follow all the prompts and go with the defaults or ok in everything you aren't sure about (use tab for picking options and arrow keys). There are two sections to pay careful attention to. First is the driver (I think its first in the order). Make sure graphics card is detected and then make sure the driver selected is "nvidia" and not "nv" or anything else. "nv" is the 2d driver to use in an emergency or problem with your display, "nvidia" is the proprietary drivers.

Next section to pay attention to is the monitor detection, make sure the monitor is detected. Then make sure the resolutions selected (you can check as many as your monitor supports) are selected. You can then specify the horizontal and vertical frequency if they aren't auto detected.

Step 3: Reboot and smile :).

That should be it, have fun with Ubuntu. I hope that was clear enough.

---

### Post by Bachstelze on 2007-06-09
> **starcraft.man said:**
> Magazine disk? They are giving Ubuntu away with magazines? Where is this?


Lots of them are doing it here, too.

---

### Post by starcraft.man on 2007-06-09
> **HymnToLife said:**
> Lots of them are doing it here, too.

Really? LOL! I didn't know this was wide spread... they certainly aren't doing it here in the French province of Canada... bah, we are always last getting stuff >.>.

Or its probably that Canada isn't very Linux centric... Not one person at my college of more than 2000 did I ever see with Linux/BSD.

---

### Post by savage.stoo on 2007-06-09
Ok that didnt go quite how I expected,

I got hold of Envy and installed its pakages, piece of cake

Clicked install Nvidia drivers (Automatic), no problems

Two dialog boxes, saying something about Xorg, clicked ok

Rebooted.
My machine then
Posted, loaded Grub, then kernel, then that nice ubuntu screen with orange progress bar.

Unfortunately this is where my smile left me, as I met a screen full of random characters trying to be a dialog box and got pushed out into what I know as command line. :(

nevermind, learning curve,

Where do I go from here?

---

### Post by starcraft.man on 2007-06-09
Odd... must have had a problem configuring the xorg automatically... ok run my command in step 2

```
sudo dpkg-reconfigure xserver-xorg
```

follow my instructions and make sure everything detects right, stick with "nvidia" as your driver this time. When your done reconfiguring issue this command:

```
sudo reboot
```

It should work after that. If that doesn't work, run the dpkg command again pick "nv" for your drivers. Post back whatever happens, it should work after your reconfigure though methinks... unless theres something else the problem.

---

### Post by savage.stoo on 2007-06-09
Yay

No funky looking screen and a nice little Nvidia X menu to play and tweak with :D

Graphics card is still showing as unknown in device manager, but its working so thats me happy

No doubt, I will be back with more problems, but until then BIG THANK YOU,

\\:D/

---

