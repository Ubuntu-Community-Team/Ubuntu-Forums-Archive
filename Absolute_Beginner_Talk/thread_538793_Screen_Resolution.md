---
title: "Screen Resolution"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by measekite on 2007-08-30
I have a Viewsonic VX2235vm driven by a BFG Geforce 6600oc card.  I can only set the screen resolution at 768x1024.  I want the native resolution of 1050x1680.  All of the information I have seen regarding this has been rather complicated.  

I went to the nvidia site and found freeBSD drivers with a complicated install proceedure and some others for Linux but do not know which to choose.

In Ubuntu I enabled the restricted nvidia driver but that did not solve the problem.

In Kubuntu I did the same with no results.  My Viewsonic monitor was not even listed in Kubuntu and I could not find any place for Display listing in Ubuntu.

Any ideas on exactly what to do.  It seems like nvidia is making things easy for windows users but not for Linux users.

---

### Post by avidnameddavid on 2007-08-30
Make sure you have the restricted NVIDIA driver installed still.  Open the terminal and use this command:```
sudo dpkg-reconfigure xserver-xorg
```Somewhere through there you will be able to select availible resolutions.  Just restart x (ctrl+alt+backspace) and login again.

---

### Post by reckless2k2 on 2007-08-30
i'm not sure but i thought you can pick a generic crt or lcd with certain resolutions. maybe not. all in all you'll have to edit the xorg.conf and modify your resolution along with horizontal and vertical refresh rates for your monitor. make sure your video card can handle those resolutions as well. i imagine they can. not sure.

---

### Post by s26c.sayan on 2007-08-30
> **avidnameddavid said:**
> Make sure you have the restricted NVIDIA driver installed still.  Open the terminal and use this command:```
sudo dpkg-reconfigure xserver-xorg
```Somewhere through there you will be able to select availible resolutions.  Just restart x (ctrl+alt+backspace) and login again.

While in the interactive reconfiguration dialog(sudo dpkg-reconfigure xserver-xorg), **make sure** you enter the correct Horizontal Refresh and Vertical Sync rates for your monitor. Personal experiences suggest this is where the screen resolutions go wrong!

---

### Post by measekite on 2007-08-30
How do you do that?

---

### Post by thetejon on 2007-08-30
Rather than specifying horizontal and vertical sync rates, I suggest choosing "Simple" when dpkg-reconfigure xserver-xorg asks, "Simple", "Medium", or "Advanced".  This will just ask you for your monitor size and then it will do the rest, saving you from specifying sync rates.  I mean, I don't have any idea what the proper sync rates are for my monitor, and I would expect you don't either.

Anyway, that's what worked for me.  If it doesn't work for you, try again and specify the rates.

---

### Post by s26c.sayan on 2007-08-30
> **measekite said:**
> How do you do that?

Do what??

You can find the horiz sync and vert refresh rates for your monitor from your hardware manuals OR by googling, if that's what you ask!

---

### Post by measekite on 2007-08-30
Can this be tested booting from LiveCD?

---

### Post by measekite on 2007-08-30
> **avidnameddavid said:**
> Make sure you have the restricted NVIDIA driver installed still.  Open the terminal and use this command:```
sudo dpkg-reconfigure xserver-xorg
```Somewhere through there you will be able to select availible resolutions.  Just restart x (ctrl+alt+backspace) and login again.

> **measekite said:**
> Can this be tested booting from LiveCD?

Can this be done using the LiveCD?

---

### Post by measekite on 2007-09-08
> **s26c.sayan said:**
> While in the interactive reconfiguration dialog(sudo dpkg-reconfigure xserver-xorg), **make sure** you enter the correct Horizontal Refresh and Vertical Sync rates for your monitor. Personal experiences suggest this is where the screen resolutions go wrong!


I solved the problem in a somewhat different way:  I understand what I did but do not understand the difference between what you suggested and what I did.  Now that I was successful it did not seem that difficult.
[B]
I used Synaptic and Terminal:

[/B]1. From the menu:  System>Administration>Synaptic Package Managerf
2. Using Search:  *nvidia-glx*  (I have a GeForce 6600
note:  For an older card you may need [I]nvidia-glx-legacy
[/I]
I installed this by clicking **apply**

After installation was complete I opened a GNOME Terminal window:
(Accessories>Terminal and typed **sudo** *nvidia-glx-config* enable

I then Rebooted the system

[COLOR=Red]**Now this is important**[/COLOR]

From the terminal:

sudo su

This temporarily gave me root permissions for the terminal session.

Type  *nvidia-settings*
This will bring up the Nvidia driver front end.  From there you can click the choices and choose the resolution and refresh rate.  Click the button to save your choices to /etc/x11/xorg.conf

Reboot and you are done.

I do not know what there is not a progrmmed installation routine for this like there is in Windows.  If there were more people would flock to Linux and then the hardware mfg would not tread Linux like the plague.

Thank you all for your help and I hope my experience will help others new to this system.  It is like I went back in time to before windows having to do some of this stuff.

---

### Post by alienexplorers on 2007-09-08
Try installing your driver using the ENVY script.  You should then be able to use nvidia-settings to set the resolution after the drivers are correctly setup.

---

