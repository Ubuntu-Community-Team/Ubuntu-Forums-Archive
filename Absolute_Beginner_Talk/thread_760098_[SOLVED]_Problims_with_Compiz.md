---
title: "[SOLVED] Problims with Compiz"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by RyanthePenguin on 2008-04-19
I have compiz and ccsm intalled but for some reason none of the changes I make in ccsm take effect.  I'm pretty sure it has something to do with my ATI graphics card, but who knows.  If you can help me out, please do, I love Ubuntu on my laptop, I want to love it as much on my desktop.

---

### Post by Saint Angeles on 2008-04-19
in a terminal, type:

glxinfo | grep direct

and give us the results

---

### Post by RyanthePenguin on 2008-04-19
direct rendring: Yes

That was all it said.  *shrug*

---

### Post by Saint Angeles on 2008-04-19
hit alt+f2 and type:

compiz --replace

---

### Post by RyanthePenguin on 2008-04-19
> **Saint Angeles said:**
> hit alt+f2 and type:

compiz --replace

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c2 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


There ya go.

---

### Post by reyhan on 2008-04-19
Go to System>Preferences>Advenced Desktop Effects Settings

---

### Post by RyanthePenguin on 2008-04-19
And then what?  None of the changes I make in Advanced Desktop Settings take effect.

---

### Post by Saint Angeles on 2008-04-19
download the latest ati driver from [www.ati.com](www.ati.com)

its 8.4 i believe

then execute it in a terminal like sudo sh ati...

then do sudo gedit /etc/default/linux-restricted-modules-common

put "fglrx" in the disabled modules (so your computer will use the new fglrx instead of the one that ubuntu has)

then open up your /etc/X11/xorg.conf and make sure you have extensions enabled...

i'm gonna attatch my xorg.conf file for kicks.

good luck.

---

### Post by RyanthePenguin on 2008-04-19
Wow.  Please forgive my inexperience, but if someone could break that down a bit farther for me.  I am downloading the ATI driver presently, however after that please go step by step in a s much detail as you can.  I'm very new here and I don't have much terminal experience.

---

### Post by Saint Angeles on 2008-04-19
are you running 64 bit or 32?

---

### Post by RyanthePenguin on 2008-04-19
32 bit

---

### Post by Saint Angeles on 2008-04-19
first go here to get the latest ati driver:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

save it to your desktop.
in a terminal, execute the file by navigating to your desktop (cd Desktop) and typing:
```
sudo sh ati[tab]
```tab will auto-complete the file name.

then go through the installer program just like you would any exe file on windows.
when its done, goto a terminal and type:
```
sudo gedit /etc/default/linux-restricted-modules-common
```in the part that reads DISABLED_MODULES="", put fglrx in between the quotations. (this will load up the new ati driver you just installed instead of the default fglrx that loads with ubuntu.) save it and close it.

now, type:
```
sudo gedit /etc/X11/xorg.conf
```paste this at the end:
```
Section "Extensions"
    Option        "Composite"    "1"
EndSection

Section "ServerFlags"
    Option        "AIGLX"    "true"
EndSection

Section "DRI"
    Mode    0666
EndSection
```under the device section, paste this above the EndSection part:
```
    Option        "VideoOverlay"    "on"
    Option        "OpenGLOverlay"    "off"
    Option        "XaaNoOffscreenPixmaps"    "true"
    Option        "AddARGBGLXVisuals"    "true"
    Option        "AllowGLXWithComposite"    "true"
    Option        "EnablePageFlip"    "true"
    Option        "AccelMethod"         "EXA"
    Option        "MigrationHeuristic"     "greedy"
    Option        "DRI"            "true"
    Option        "TexturedVideo"        "on"
    Option        "UseFastTLS"        "0"
    Option        "BlockSignalsOnLock"    "on"
    Option        "KernelModuleParm"    "locked-userpages=0"
    Option        "ForceGenericCPU"    "off"
```save it and reboot. cross your fingers.

P.S. I'll attatch my xorg.conf file for kicks!

{EDIT} If the latest fglrx doesn't work for you, try clicking on "previous drivers" and trying an older one.

---

### Post by RyanthePenguin on 2008-04-19
Saint Angeles,

You are my hero!  Thanks, I appreciate all of your help.  I swear, the community support is what makes Ubuntu great.  Thanks for helping a newb out.

---

### Post by trickyarcher on 2008-05-03
Saint Angeles,

I want to thank you for all your efforts.  However, I am still unable to get anywhere with my ATI card and DRI.  I am attaching my xorg.conf.  Maybe you can point me in the right direction.

I have tried everything from ubuntu Binary ATI install, ATI Linux wiki, EnvyNG, and Ed Hewitt's fix at [http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/]("http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/") but nothing seems to be able to help me resolve the following:

```

:~$ less /var/log/Xorg.0.log |grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Failed to open DRM connection
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): No DRM connection for driver fglrx.
(WW) fglrx(0): could not detect X server version (query_status=-3)
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Option "AddARGBGLXVisuals" is not used
(WW) fglrx(0): Option "AllowGLXWithComposite" is not used
(WW) fglrx(0): Option "EnablePageFlip" is not used
(WW) fglrx(0): Option "AccelMethod" is not used
(WW) fglrx(0): Option "MigrationHeuristic" is not used
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) Configured Mouse: No Device specified, looking for one...

```

or. . .

```
:~$ less /var/log/Xorg.0.log |grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 

```

If I can provide any more information to help people solve this, let me know and I will give it to you.

Thanks,
Tricky

---

### Post by Saint Angeles on 2008-05-05
hey there!
it looks to me that you may have something wrong with your xorg.conf...
try running this to reconfigure your xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
this will make a default xorg.conf file with default values... then try adding the things in my post there (dri, 0666, composite...)

if the latest fglrx doesn't work, theres a chance that the older ones will work:
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
select your card from the list and there should be a link with "previous drivers"...

i've noticed that april's fglrx doesnt work for me but march's is perfect. lemme know how that works... and your new xorg.0.log with any errors if it doesnt.

---

