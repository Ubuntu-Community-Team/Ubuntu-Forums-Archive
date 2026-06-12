---
title: "usb modem installation problem"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by graham bowers on 2008-02-22
Hello
I'm yet another ubuntu newnewnewbie and so far it's been a very positive experience, but I'm unable to get a dialup modem to work. 
The machine in question is a compaq NX6110 and I was getting nowhere (think it's a winmodem on board ) so I bought a Zoom usb modem today, model 3095 because it said linux on the box :-))
[http://www.zoom.com/products/dial_up_external_usb.html](http://www.zoom.com/products/dial_up_external_usb.html)

Anyway I followed the destructions about how to install the linux drivers provided, and it seems three flavours are on the CD, rpm, debian, and tar. As ubuntu is a derivative of debian I tried to install that (having worked out how to use the terminal and sudo command) and I got a message that basically said that there was not a suitable driver.

So, I'm a bit stumped right now and could do with some pointers please?
Sources for a driver, or a suggestions for a modem that will just work.

Broadband works fine, just plugged ethernet in and bingo!

I need dialup as I want to loan the machine to my mother so she can try out "the internet" on dial up pay as you go, before she decides if she wants to commit to a broadband account.

Cheers
Graham

---

### Post by spiderbatdad on 2008-02-22
It sounds like you will need to blacklist the onboard modem in /etc/modprobe.d/blacklist. Plugin your new modem and run ```
sudo wvdialconf
``` to see if the device is detected. If it is not you could try running lsusb and then modprobe the modem and try again to detect it. Dial-up can be a real pain, but easier with a usb modem than with a soft modem, generally. Do a little googling. There are a number of good guides to configuring a usb modem in Ubuntu.

---

### Post by zoomzoomzoom on 2008-02-29
I just posted under laptops and hardware how I got my Zoom 3095 working under Ubuntu 7.10 "Gutsy" live cd.  I dont regularly use Ubuntu, just using it as an experiment because I had the Ubuntu cd and there exists a precompiled driver for it.  Not sure any differences on a full install as opposed to running as live cd.  But it does work.  Just make sure your kernel matches exactly if you go for the precompiled binary pkg of the driver on linuxant.com site.  [http://ubuntuforums.org/showthread.php?p=4431499#post4431499](http://ubuntuforums.org/showthread.php?p=4431499#post4431499)

---

