---
title: "Ubuntu 7.04 device manager"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by mlucian72 on 2007-06-13
I am trying to see what hardware are installed (supported) and what is not, so I opened device manager, like I would normally do in windows, and found all my hardware. I don't know if there are any red or yellow icons next to the items that don't have a driver installed, like there is in windows, but I don't see any. All my devices have either a light gray icon, or a darg grey/green icon next to them.
 How do I make sense of this?
 Is there a way to know what device on the computer doesn't have a driver installed?

  Thanks! ;)

---

### Post by starcraft.man on 2007-06-13
> **mlucian72 said:**
> I am trying to see what hardware are installed (supported) and what is not, so I opened device manager, like I would normally do in windows, and found all my hardware. I don't know if there are any red or yellow icons next to the items that don't have a driver installed, like there is in windows, but I don't see any. All my devices have either a light gray icon, or a darg grey/green icon next to them.
 How do I make sense of this?
 Is there a way to know what device on the computer doesn't have a driver installed?

  Thanks! ;)

Uh, ya I know what your talking about. That device manager (Hardware Information in the Preferences section) isn't the best just yet. I don't use it often or ask other people to.

To see all the PCI things slotted in your computer use this command:

```
lspci
```

to see the USB devices use:

```
lsusb
```

A note on these two commands, they won't show you how the drivers are just the hardware. And you need to issue the commands in the terminal (Applications > Accessories > terminal).

Most hardware works on the default Ubuntu drivers very well. Mice and keyboards always work out of the box, exception is the special keys that require custom xorg but most can be found on the forums or asked. Integrated sound cards on the intel and other mobos work very well, the only trouble in that area is if you have third party cards like creative audigy cards, those need separate drivers to work. The only other thing you need to worry about is graphics cards, Ubuntu doesn't support any 3D drivers out of the box and you need to install them either via Restricted Driver Management or [Envy.]("http://albertomilone.com/nvidia_scripts1.html")

While I'm talking about restricted driver management, this is a good feature to help you. If you go System > Administration > Restricted Driver Management, Ubuntu scans your PC for products without drivers that need proprietary ones that are available. Things like graphics card drivers can be installed by this, I assume in the future it will be expanded to install many more things.

Everything else generally works very well like USB (firewire too I think), ethernet connections, networking and printing. Wireless is the really sore spot in Linux, search for ndiswrapper and your custom card on the forums and try your best getting it working. Then ask for help if it fails.

Thats about it for main hardware, webcams and other assorted but optional peripheral should be tested and if not working searched on the forums for drivers specific to the product. 

Hope that helps best of luck with Ubuntu : ).

---

### Post by mlucian72 on 2007-06-13
Thank's a lot for the response.
 I don't have any problems, but I just wanted to see if all my hardware is installed. The only thing not working is the web cam, but I'm trying to find a driver for it.
 I am really impressed with Ubuntu...it installed fast and everything worked perfect the first time.
 I am really a newbie, but I'm trying to learn as much as I can.

 Thanks for the reply! :D

---

### Post by starcraft.man on 2007-06-13
> **mlucian72 said:**
> Thank's a lot for the response.
 I don't have any problems, but I just wanted to see if all my hardware is installed. The only thing not working is the web cam, but I'm trying to find a driver for it.
 I am really impressed with Ubuntu...it installed fast and everything worked perfect the first time.
 I am really a newbie, but I'm trying to learn as much as I can.

 Thanks for the reply! :D

No problem, I will give you links for learning more than since you seem so excited :D.

[Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") site and [psychocats]("http://www.psychocats.net/ubuntu/") for General basics. [LinuxCommand]("http://www.linuxcommand.org/") for learning the CLI/Terminal. [Ubuntu Wiki]("https://wiki.ubuntu.com/") for advanced and specific questions (also forums of course) [Linux app finder]("http://linuxappfinder.com/") for finding programs and applications that suit your needs.

Oh and Envy like I linked to for drivers, I prefer it over the management....

Have fun, there is lots to know but its great to know and you will find so many more powerful features in Linux. Oh and if you like Video tutorials check the beginning of Ubuntuguide for a list of em.

---

### Post by mlucian72 on 2007-06-13
Thanks again! Great links!

---

