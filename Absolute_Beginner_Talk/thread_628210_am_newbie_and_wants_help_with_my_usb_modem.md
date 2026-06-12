---
title: "am newbie and wants help with my usb modem"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by zerofreeze on 2007-12-01
can u tell me what to do after installation of SpeedTouch330_firmware_3012.deb
i've done the following:
sudo cp/user/share/doc/ppp/examples/peers-pppoa/ etc/ppp/peers/adsl
gksudo gedit /etc/ppp/peers/adsl
gksudo gedit/etc/ppp/pap-secrets
gksudo gedit/etc/ppp/chap-secrets

and when i rebooted and typed "pon adsl" in terminal it said "Plugin pppoatm.So loaded" but the networking connection still has a red "!" sign on it ...

can u kindly help me

---

### Post by ukblacknight on 2007-12-23
Bump.  Any one got any ideas about this, i'm having the same problems.  On the peers file, i've set the VCI (or whatever it is) to 38, as that what it says in Windows, and VPI to 0.

sudo pon speedtch (thats the way i've got it setup) loads the file, but then says device (0.38 ) not found.

I'm using Tiscali, with the USB modem plugged directly into the machine.

---

### Post by Duck2006 on 2007-12-23
Have you looked in the
System>>Administration>>network
and configured it in there?

---

### Post by plucky on 2007-12-24
ukblacknight

check out this location:

[http://www.squeezedonkey.com/wiki/linux/index.php?title=How_to_Try_it](http://www.squeezedonkey.com/wiki/linux/index.php?title=How_to_Try_it)

for information on how to install a package created by Stephan Harper for the **Speedtouch 330 USB modem**. From there it will point you to the location of the package to install on your system.

Also check out this thread in **Network and Wireless** forum for more information

[http://ubuntuforums.org/showthread.php?t=585647](http://ubuntuforums.org/showthread.php?t=585647)

This makes installing the Speedtouch very easy.

Cheers

---

### Post by ukblacknight on 2007-12-24
I tried usbadslmodemmanager and it doesn't work for me, I start it up, and the tooltip says "starting up...".  I enter my ISP details, click OK, click connect, and it still says "starting up..." and nothing happens.  If I unplug the modem, start the manager up, plug in the modem and click connect, the same thing happens.

I think the firmware is installed ok - both green lights on my modem stay solid as soon as the kernel boots up.

Is there any way of diagnosing this issue?  I can pipe the output of 'usbadslmodemmanager' if you wish?

---

### Post by plucky on 2007-12-24
ukblacknight

1)Do you get the icon in the system tray,i.e top right hand of screen?
2)What version of usbadslmodemmanager did you download?

When **usbadslmodemmanager** starts up the first two bars are grey and the third green.When you connect they all go green.

To trouble shoot the startup ,it is best to use the terminal to start it up as this will give you any error messages it encounters.Also you can use the **dmesg** in terminal to see any errors in the system logs.

You might have to unplug and plug it in a couple of times.Once it is set up and working you should only have to click on the icon and connect.

Good luck

---

### Post by ukblacknight on 2007-12-24
Yeah I get the system tray icon, however its all grey with no green bars.  It stays like that all the time.

Some errors do show up, however they usually show up with other commands, I think its something to do with my theme i've got, I'll try changing it and seeing if that changes things.

The version i'll check in a minute, however I downloaded it yesterday so it should be the latest.  Ill get my output from the terminal now...

Cheers
ukblacknight

---

### Post by ukblacknight on 2007-12-24
Fixed it!  I changed my theme to just standard clearlooks, and that enabled the program to continue.  The errors must of been stopping it from continuing.  All connected now :D

Cheers plucky. :D

---

