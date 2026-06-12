---
title: "Flatscreen Display Position Woes"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by dglp on 2006-11-22
I have just set up Kubuntu 6.10 (Edgy Eft) on my desktop machine. Of the issues I'm trying to resolve, one of the most annoying is that the display is shifted left or right (depending on boot status) on the monitor by tens of pixels. When booting, the text is shifted *left* off the screen by several characters so I cannot read lines of text. Once Kubuntu is running, the GUI is shifted *right* several pixels, slightly more than the width of the vertical scrollbar. 


My monitor is a [Samsung Syncmaster SM770P]("http://www.samsung.com/uk/products/monitors/lcd/digital/ls17vdpxhqedc.asp?page=Specifications"), and my VGA card is an Nvidia [GeForce FX5200]("http://www.nvidia.com/page/fx_5200.html"). The monitor has no hardware adjustment keys (thought there'a a Windows-based suite called MagicTune), and I have no idea if GeForce provide Linux-based calibration tools (such as nView). A quick query of Adept shows several possibilities - but I'm not sure which of these to use. 

So, given the left-right shift, I may have one problem, or two. Any suggestions? comments?

---

### Post by o_fortuna on 2006-11-22
First of all, are you using the default driver (nv)? I had a similar problem once with my nvidia driver. It could be the monitor -- I changed monitors and it worked. Anyway, you might try using nvidia drivers by going into Adept and installing nvidia-glx and then running
```
sudo nvidia -xconfig
```
to set up the drivers. Then log out and press Ctrl+Backspace to restart X and try again. I really don't know if this will work, though -- sorry. It's a funny problem that (I think) might possibly perchance have to do with drivers.

---

### Post by mgmiller on 2006-11-22
I own 3 different Samsung LCD monitors and they all have adjustment buttons.  On your monitor, they may not be obvious.  Look underneath the bottom edge of your screen, or on the back or sides.  The problem you are seeing is happening because during boot, your video card sends a different set of refresh rates / resolution signals than it does once x starts.  In both cases, you would only have to hit the "automatic" button on the monitor, while it is displaying the screen in question and it will readjust it and remember it.  Really look closely at your monitor, turn it upside down if you have to and look along the edges for the buttons.  Samsung is really good about giving lots of hardware adjustments for their monitors.  The only other thing I can think of is if you are using an analog cable to connect it, (VGA) switching to digital (DVI) usually does away with all these issues.

---

### Post by dglp on 2006-11-23
Hi both, and thanks for the tips. But I have made things worse by running the X server.

I have checked the driver (nv) and the monitor (only one button, for power on/off). I've loaded the glx driver (note that it's nvidia-xconfig, no space before hyphen). It sends the machine into a command-line mode at restart, with the same problem that the display is shifted offscreen by 3 characters - so I cannot read the text. This must be an X server, but I know nothing about how to work in it, nor even how to exit and reboot normally. For instance, I need to become root, and enter a stop command, and don't know how to do either of those things. Oops! 

Am I going to have to reload the OS from scratch now?

---

### Post by rosegarden78 on 2008-01-19
A clean install of Gutsy or latest distro usually works if you backup.  If no solution is found try waiting for next distro or fall back to your previous OS (yuck) in the interim.  I'm sure the engineers are working on it.  If it works in Mac/Win it's only a matter of time before it's ported to X.

...wait...did you say X crashed on startup?  That happens when you make a mistake in your /etc/X11/xorg.conf file.

Using Edgy (Gutsy is perfect!) this happened and I didn't know that because I was a n00b and first time Linux user.  Just the other day I left one wrong letter in xorg.conf in Gutsy and I got the terminal at startup.  If you backed up your /etc/X11/xorg.conf file just restore it.  It also could be that your hardware isn't supported yet although Ubuntu runs my HP printer out of the box with hp-tools better than the CD-ROM does on Mac/Win.  But if you don't know the terminal commands you should learn a basic text editor and how to mount disk drives from the fstab / mtab.

sudo nano /etc/X11/xorg.conf

So be careful with xorg.conf and backup or comment your changes.

Don't use Beryl/Compiz with Edgy!

Use Gutsy Gibbon 7.10+ or fall back to Mac/Win.

---

### Post by erutufon on 2008-01-29
mg miller
hi am using a samtron tft screen, with similar problem to above (screen shifted left by 10-20 pixels).  read your post and found a new button on the bottom of the monitor, problem solved - many thanks!

---

