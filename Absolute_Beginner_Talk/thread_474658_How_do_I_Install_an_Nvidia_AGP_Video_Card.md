---
title: "How do I Install an Nvidia AGP Video Card?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-06-15
Fellow Ubuntuns: Because the Via chipset on my PC Chips M861G mobo froze on any 3D apps. I bought and attempted to install a GEForce 5200 AGP video card, in part because one reviewer on Tiger Direct recommended it for Ubuntu. The documentation recommended going into the BIOS and deselecting the mainboard video; the only entry I could find was to select AGP as the primary video card location. But when I boot, I get an error that says that the X-windows system doesn't recognize the card. I ran:

sudo apt-get install nvidia-glx-new (or something like that)

but got the same result. I tried to run Xserver Xconf, but couldn't find the Nvidia driver to select on the first page. So now I have a Ubuntu box that won't Ubuntu, other than by command line. I've read enough posts to see that this can be a difficult situation. I did get a CD with the card, but assume that that is for Windows only. Does anyone have any troubleshooting suggestions?

Thanks!

---

### Post by overdrank on 2007-06-15
> **wmichaelb said:**
> Fellow Ubuntuns: Because the Via chipset on my PC Chips M861G mobo froze on any 3D apps. I bought and attempted to install a GEForce 5200 AGP video card, in part because one reviewer on Tiger Direct recommended it for Ubuntu. The documentation recommended going into the BIOS and deselecting the mainboard video; the only entry I could find was to select AGP as the primary video card location. But when I boot, I get an error that says that the X-windows system doesn't recognize the card. I ran:

sudo apt-get install nvidia-glx-new (or something like that)

but got the same result. I tried to run Xserver Xconf, but couldn't find the Nvidia driver to select on the first page. So now I have a Ubuntu box that won't Ubuntu, other than by command line. I've read enough posts to see that this can be a difficult situation. I did get a CD with the card, but assume that that is for Windows only. Does anyone have any troubleshooting suggestions?

Thanks!

Hi, after the xorg warning get to command prompt and  enter the command sudo dpkg-reconfigure -phigh xserver-xorg ,and it will configure your xorg and then you can use envy to install the proper graphics drivers.

---

### Post by wmichaelb on 2007-06-15
Overdrank: Entering that command put the Nvidia drivers as a selection into the xserver-org menu; they were missing before. I selected Nvidia, rebooted and everything runs. Woo-hoo! It even runs all the screensavers and Penguin Racer!

Thankyouthankyouthankyou.

For the benefit of others (and perhaps myself down the line), is there any sort of documentation or process for installing video cards somewhere on Ubuntu.com, other than asking for help on this forum? I searched, but couldn't find one, and don't know enough yet to write one.

---

