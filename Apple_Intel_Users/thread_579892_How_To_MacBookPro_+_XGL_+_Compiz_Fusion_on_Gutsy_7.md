---
title: "How To: MacBookPro + XGL + Compiz Fusion on Gutsy 7.10"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by linkx on 2007-10-18
Now that Gutsy is all fresh off the press, Mac Book Pro owners (before nVidia became the GPU) are wondering if this new Compiz Fusion desktop effects integration will work with their ATI-graphics MacBook Pro. **Well, it won't**. Unless you do this:

[LIST=1]
[*]Install Ubuntu 7.10 final
[*]Use **System > Administration > Restricted Drivers Manager** to install the** ATI (fglrx)** driver 
[*]REBOOT
[*]Open **Applications > Accessories > Terminal** and type 
```
sudo gedit /etc/X11/xorg.conf
```Then hit **Enter**
[*]Scroll to the bottom of the file and look for this: ```
Section "Device"
```
Then paste the following into the "Device" section: 
```
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "on"
```
Add these sections to the *bottom* of the file (not within any other section):
```
Section "ServerFlags"
        Option "AIGLX" "off"
EndSection
Section "DRI"
	Mode 0666
EndSection

```
[*]Save xorg.conf and quit gedit
[*]Install the following packages by returning to ** Applications > Accessories > Terminal** and pasting:
```
sudo apt-get install xserver-xgl dbus-x11 compizconfig-settings-manager
```Then hit **Enter**. 
**Note:** *We no longer need to create special start-up scripts and GDM menu entries to get into an XGL Gnome session!*
[*]REBOOT
[*]You will now have Compiz Fusion desktop effects enabled when you log in. To edit these effects, use **System > Preferences > Appearance > Visual Effects Tab > Custom > Preferences**
[/LIST]
See my attached screenshot for the Expo plugin in action. I have an external monitor that is the same resolution as my MacBookPro. It works great with Compiz Fusion and can be enabled by adding the following to the "Device" section of xorg.conf:
```
Option "DesktopSetup" "horizontal"
Option "DesktopSetup" "AUTO,AUTO"
```
and then reboot. 

This guide should apply to all ATI graphics computers that use the fglrx non-free restricted driver. Let's hope that ATI will help get the AIGLX system working with fglrx so that this How-To is made obsolete! Hope this helps y'all!

Link

---

### Post by changty on 2007-10-18
I did like you adviced here, but i can not get compiz up and running. With XGL running i get this error-message with glxinfo:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Segmentation fault (core dumped)


Compiz just freezes the whole system if i try to launch it, it wont do it by it self.

Any ideas what's wrong? And i have 20" alu imac with hd2600, but i got that already running with fglrx :)

---

### Post by maluka on 2007-10-20
thanks. how do i add themes?

---

### Post by Can+~ on 2007-10-20
> **maluka said:**
> thanks. how do i add themes?

On 7.10:
System > Preferences > Appearance > tab Theme > Install (at the lower right), select the .tar.gz (or .tar.bz2.. etc) file and you're done.

On 7.4:
System > Preferences > Themes > Add theme (right menu), select the .tar.gz (or .tar.bz2.. etc) file and you're done.

Where to get Gnome themes?

[http://www.gnome-look.org/](http://www.gnome-look.org/)
[http://art.gnome.org/](http://art.gnome.org/)



Btw, if you use FGLRX on the macbook, can you enter the desktop without workarounds/troubles (like restarting the xorg)?

---

### Post by JayKay1967 on 2007-10-21
Trying to get 3d effects working in Gutsy on my MBP but going round in circles.  This was the most promising thread I found in two days of searching but still haven't gotten 3d effects working.

I've followed the steps above and have loaded restricted drivers etc but must have done something wrong along the line....

for some reason the  ATI (fglrx) driver never seems to stay selected.  When I go into the screen driver settings it keeps defaulting to VESA?!

I can access the customised setting for 3d effects and select items such as 3D cube etc but nothing seems to happen.

Anyone welling to help me out?

Regards

Jay

MBP c2d 2.33Ghz/3Gb RAM
ATI X1600 256mb
Ubuntu Gutsy Gibbon 7.10 via VM Fusion version 1.1b1 (57919)

---

### Post by cyberdork33 on 2007-10-21
> **JayKay1967 said:**
> for some reason the  ATI (fglrx) driver never seems to stay selected.  When I go into the screen driver settings it keeps defaulting to VESA?!
That is strange. Did you restart after installing fglrx?

---

