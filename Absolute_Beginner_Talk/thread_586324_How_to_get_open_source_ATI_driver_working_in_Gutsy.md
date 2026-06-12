---
title: "How to get open source ATI driver working in Gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by DrQuincy on 2007-10-22
When I did the upgrade to Gutsy my display broke.  I'm in low graphics mode now on a pathetic 800 x 600.

I have had no luck with the closed source driver (I have X1300 Pro by the way and when I enable the driver in RDM it goes black when I reboot) and have given up on Compiz.

I just want my 1680 x 1050 back now but can't seem to do it.

I've reconfigure xserver-xorg loads of times, I've reinstalled it but no luck.  My xorg file looks correct.  It is trying to use the ati driving but something is going wrong and it's defaulting to vesa.

Where the X server error log?

Also, I've tried the System > Administration > Screens and Graphics to no use.  If I select ati from the driver dropdown it shuts the window down and goes back to 800 x 600.  If I choose LCD 1680 x 1050 from the monitor section to try to select it by brand it goes fuzzy when I test it.

Any ideas how I can fix this?  I just want 1680 x 1050 back, I'm not bothered about Compiz Fusion.  What the best way to get the open source ATI driver working at this stage?  Is there any way to wipe the settings and start again?

All help appreciated. :)

---

### Post by Ant_Merlin on 2007-10-22
Hello, what you need to do is first go to restricted drivers in system>administration and select driver, it will ask to install a driver, let it install.

You may have to reboot and it may again run in low graphics mode, if it does choose fglrx from the driver menu and at the bottom select propreity driver rather than open source.

if it doesnt ask you to reboot, you will need to anyway.

fglrx propreity will work. I have an X1650 and its the only driver that worked for me. now everything is fine.

---

### Post by DrQuincy on 2007-10-22
> **Ant_Merlin said:**
> Hello, what you need to do is first go to restricted drivers in system>administration and select driver, it will ask to install a driver, let it install.

You may have to reboot and it may again run in low graphics mode, if it does choose fglrx from the driver menu and at the bottom select propreity driver rather than open source.

if it doesnt ask you to reboot, you will need to anyway.

fglrx propreity will work. I have an X1650 and its the only driver that worked for me. now everything is fine.

Thanks for your reply (and I'm jealous that you got it working :)).

However, when I do that and restart I just get a black screen and have to dpkg-reconfigure X.  What's strange is, when I first checked the driver in the RDM it didn't ask to install a driver.  Any ideas why?  Is there anyway to reset any settings and ask it to install the driver again?

---

### Post by Ant_Merlin on 2007-10-22
Hello, on screens and graphics i had 2 boxes, i selected both on fglrx propriety drivers. it did work eventually, did you select propriety rather than open source? you could try fbdev? that one also worked for me.

I have since done a clean install and think it works better (did that last night and runs very well)

try fbdev driver.

---

### Post by DrQuincy on 2007-10-22
Sorry for being stupid but what's the fbdev driver and how do you install it?

---

### Post by Ant_Merlin on 2007-10-22
when you select from the list of drivers in screens and graphics there is a driver that says fbdev, this also worked for me.

---

### Post by spinetingler on 2007-10-22
I have the restricted driver installed and working but when I try to enable desktop effects this is the error message I get "The Composite extension is not available"... Any help?

---

### Post by Ant_Merlin on 2007-10-26
hello, this means you haven't installed the xgl server.
goto synaptic manager and search for xserver-xgl. install this and then search for compizconfig-settings-manager. install that. restart and you will be able to set extra effects. you will also have an icon in system>preferences that says Advanced Desktop effects settings and this will alow you to configure compiz.

---

