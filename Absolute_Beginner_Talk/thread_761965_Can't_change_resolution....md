---
title: "Can't change resolution..."
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by khr on 2008-04-21
I changed the color depth to 16 bits, don't ask why.
I restarted and it was just a black screen.
I went into recovery mode and entered:
"sudo dpkg-reconfigure xserver-xorg"
After all that, i came to the monitor part.
I chose 1280 x 800 as resolution (Which it normally is...) and 24 bits as depth.
I completed it and typed "exit".
Ubuntu started up and the resolution was on 1024 x 768.
I've repeated "sudo dpkg-reconfigure xserver-xorg" 4 times.(Choosing 1280 x 800 as resolution of course) It didn't have any effect...

So now I'm stuck with 1024 x 768 as resolution and thats frickin ugly.
How do i change it back to 1280 x 800? I'm desperate! The current resolution is
melting my eyes!!!

---

### Post by phidia on 2008-04-21
For some reason X isn't recognizing that setting. Has anything else been changed in your /etc/X11/xorg.conf file?

Look to see if the correct driver is selected and check what resolutions are listed too.

You can try editing that conf file and putting in the resolution(s) you want.

---

### Post by khr on 2008-04-21
I've tried several different options but it just results in black screen or low resolution. But i've found out that my ATi video card is disabled and it need to be enabled so that ubuntu can run on 1280 x 800. 
 I enabled it and it asks for a restart.
When i restart my laptop and start ubuntu again, theres just a black screen. So i think i need a driver for the video card...

Please help!

PS: You wont be seeing me before tomorrow...

---

### Post by Weijyan on 2008-04-21
I am having a similar problem.  I installed Ubuntu 7.04 this morning on a system that had previously run Windows XP Pro.  My resolution in XP was 1600 x 1200, but the Ubuntu resolution is stuck at 800 x 600 with no other options available.  I just installed it and, even before the updates, this was the only option.   I updated it, hoping that the updates would allow me to do the things I could not (increase resolution, dual monitors, ect), but even the monitor mirroring went away after updating.

If 1600 x 1200 is not something available in Ubuntu, that is fine, but I want something higher than 800 x 600.  In virtually all of the applications, the control buttons are below the toolbars and I cannot do anything but try to move around the tool bars to get to them

Also, is there any way to run dual monitors on Ubuntu?  If it is there, I must be missing it.

---

### Post by banished_one on 2008-04-22
get ENVY from albertomilone.com/nvidia_scripts1.html

---

### Post by khr on 2008-04-22
> **banished_one said:**
> get ENVY from albertomilone.com/nvidia_scripts1.html

Thanks, but it didn't help...
I tried automatic and manual install several times.
I've also tried changing the driver for my graphic card into Radeon(Vesa), Radeon(fglrx) and fglrx. Any of them just results in black screen.
When i reconfigure the xserver-xorg by using "sudo dpkg-reconfigure xserver-xorg" i always choose vesa. I've tried ati and fglrx but they just result in black screen.

Just to remind you about the main problem(for me, at least):
When i enable my restricted ATi driver then restart the computer, i just end up with a black screen...

---

### Post by khr on 2008-04-23
Bump
Please help!

If it helps, I'm using:
ATi Mobility Radeon X1600 512MB

---

### Post by bred on 2008-04-23
> **khr said:**
> 

Just to remind you about the main problem(for me, at least):
When i enable my restricted ATi driver then restart the computer, i just end up with a black screen...

[COLOR="Blue"]listen,
I had the same problem as you - black screen after enableing restricted drivers...I have an old geforce 460 - 64mo
tried different solutions - and nothing...same black screen..
my solution was not to use restricted drivers
that's it :)[/COLOR]

---

### Post by Fire_Chief on 2008-04-23
The driver may be working fine but Xorg may not have the correct info for your monitor. This will directly affect the available resolutions on the desktop. A correct monitor definition is very important for Xorg to know how to display the gui.

If you have your monitor's manual, look in there and find the Horizontal sync and Vertical refresh rates. Then either custom define your monitor in the *sudo dpkg-reconfigure xserver-xorg* wizard or manually input them into the xorg.conf file under your monitor definition. Mine looks like this..```

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1400x1050"
        Horizsync       31.5-65.5
        Vertrefresh     56.0 - 65.0
EndSection

```

The sync/refresh ranges specified allow me to choose any screen resolution from 320x200 all the way up to 1400x1050.

You should be sure to set the numbers/ranges appropriately!!!  Incorrect settings could really mess up the display and (rarely) your monitor.

Cheers!

---

### Post by Weijyan on 2008-04-25
As suggested, I d/l'ed and installed Envy and used it to uninstall, then re-install my video drivers.  It actually ended up making it worse.

My resolution is now stuck at 640 x 480 on my primary screen.  It *does* give me the option to turn on multiple monitors, but it will not actually *allow* me to do it.  In the rare occasions I can actually get to the buttons, it gives me a message that it could not be applied.

I am currently downloading the upgrade to 7.10 in the hope that will allow me to do something.

---

### Post by bhursey on 2008-04-25
I had to add the following to the Screen section of xorg.conf after I enabled the restricted nvidia drivers in 7.10 and 8.04. For the old school people there was no fancy gui to set resolutions when I started using debian in 2000 :P Back then I even compiled my kernel from scratch. You had to also manually configure /etc/X11/xorg.conf.  I remember it took me 2 weeks of trying before I was able to get my wireless working on my old dell insperon 8000... ok Enough remonising. Hope it works for you. Recommendation. If you are going to use Linux, start learning the underlying os and configuration files. Would you trust your life to a gui? 

  ```
  SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
```

---

### Post by Weijyan on 2008-04-27
I plan to learn, I just have not had enough time to really play around with it.  Thanks for the suggestion.

---

