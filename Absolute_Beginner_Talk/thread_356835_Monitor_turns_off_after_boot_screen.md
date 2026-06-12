---
title: "Monitor turns off after boot screen"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by thorst on 2007-02-08
I am very new to linux, ive installed mandrake a couple times (when it was mandrake) but i've never done anything with ubuntu.

The question: I installed Xubuntu 6.10 on an old machine. around 800 mhz, 256 mb ram, old video card, and 120 gig hdd. Basically I need to set up a web server on a budget ($0). 

After installing was completed and it rebooted it will show the loading screen with the silver bars going across the bottom of the logo and then once its done the monitor will stop recieving a picture. The green light on the monitor turns orange but the computer is still running. Im guessing this is a driver issue with my video card? but if thats the case why would it display anything at all. And this is pretty old hardware so i think they would have drivers for it already. 

Some background so we can skip the extreme basics-
Any way like i said im new to this, i come from windows, I am a programmer (tcl) and used to be network admin at my last job so im not an idiot. I have a lot of expiriance just not with this.

---

### Post by spin2cool on 2007-02-08
My guess is that it's a video card issue and you'll have to muck around with your xorg.conf.  

To start, try booting into CLI mode and use "sudo dpkg-reconfigure xserver-xorg".  Walk through the steps and see if you can get it booting that way.  

Also try searchign for your specific video card on these forums and elsewhere.  It's a safe bet that someone has had this problem and solved it before.

---

### Post by nickburns on 2007-02-08
You can post up your xorg.conf file.

It is found at /etc/X11/xorg.conf


also let us know what video card you have and monitor.

---

