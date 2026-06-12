---
title: "Help getting Compiz to work"
date: 2011-02-16
forum: Apple Hardware Users
---

### Post by bug67 on 2011-02-16
Just installed Maverick on my dual 2.7 PowerPC G5.  The results of: 

```
lspci | grep ATI

0000:f0:10.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
```

I would like to enable compiz desktop effects.  The info I have come across so far is cryptic and incomplete.  Could someone be kind enough to walk an absolutely clueless n00b through the process.  TIA.

---

### Post by jwcalla on 2011-02-16
Try System -> Preferences -> Appearance -> Visual Effects and select either Normal, Extra, or Custom.  You might need to install the proprietary video drivers from ATI.

If you need to get the proprietary drivers, try System -> Administration -> Additional drivers and activate "version current" or the latest available version.

---

### Post by bug67 on 2011-02-16
If only it were that easy.  We're talking *PowerPC* here.  ;)

---

### Post by jwcalla on 2011-02-16
omg... try upgrading to an UltraSPARC... :-#

Yeah I think you can rule out the proprietary drivers.

---

### Post by realzippy on 2011-02-16
There is no proprietary driver for your (old) card.
The free ati driver should work out-of-the-box...

---

### Post by bug67 on 2011-02-16
There is a way to do it I just don't understand what I'm reading.  The instructions seem incomplete to me:

[http://www.uluga.ubuntuforums.org/showthread.php?p=9194781#post9194781](http://www.uluga.ubuntuforums.org/showthread.php?p=9194781#post9194781)

> **realzippy said:**
> The free ati driver should work out-of-the-box...

I cannot enable desktop effects (Compiz) with the built in ATI drivers.

---

### Post by realzippy on 2011-02-16
> **bug67 said:**
> There is a way to do it I just don't understand what I'm reading.  The instructions seem incomplete to me:

[http://www.uluga.ubuntuforums.org/showthread.php?p=9194781#post9194781](http://www.uluga.ubuntuforums.org/showthread.php?p=9194781#post9194781)



I cannot enable desktop effects (Compiz) with the built in ATI drivers.

..was also doing a little search and found this:
[http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx](http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx)

..which is nearly the same as your link.
Think it is just using a xorg.conf and a kernel boot option...
give me a minute to clarify.

---

### Post by realzippy on 2011-02-16
```
gksudo gedit /etc/modprobe.d/radeon-kms.conf
```

creates the empty file where you paste in:

```
options radeon modeset=0

```
close & save file.

```
gksudo gedit /etc/X11/xorg.conf
```

creates empty xorg.conf file.Paste in:

```
Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
    BusID        "PCI:0:16:0"
    Option        "DynamicClocks" "true"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "true"
    Option        "UseFBDev" "false"
    Option        "DRI" "true"
    Option        "GARTSize" "64"
    Option        "AddARGBGLXVisuals" "true"
    Option        "XAANoOffscreenPixmaps"
    Option        "DisableGLXRootClipping" "true"
    Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection
```

close & save file.
**Reboot!**

If problems rebooting,boot in recovery mode,drop to shell and delete
the xorg.conf (print/write down)

```
sudo rm /etc/X11/xorg.conf
sudo reboot
```

---

### Post by bug67 on 2011-02-16
"Close and save file" = ctrl+x?

---

### Post by realzippy on 2011-02-16
close the "gedit" window applying changes..








edit:
sorry important soccer match ahead..back 2hours

---

### Post by bug67 on 2011-02-16
Update Manager is chewing on a bagillion things right now.  As soon as its done, I will report back with the results of the tutorial...

---

### Post by bug67 on 2011-02-16
OK, wow.  That totally didn't work!  :-?

I'm tired.  I *may* mess with this later.

I think the xorg file wasn't specific to my set up and completely borked everything.  I was able to delete it from the shell and reboot but, then everything was all wonky.  I.E. was only able to use one monitor, weird graphic artifacts, too much for me to want to try and sort through.  I may just have to settle for life without desktop effects on this machine?

Thanks though.  I guess Apple's planned obsolescence applies even when wanting to use Linux.

---

### Post by realzippy on 2011-02-16
```
sudo rm /etc/modprobe.d/radeon-kms.conf
```

..makes sure that your displays are controlled by KMS as formerly.
Everything should work as before.If not,then your updates you ran may
cause this.
You should have mentioned that you run a dual display setup;the
xorg.conf should have been modified then.
BTW,compiz with free ATI driver and 2 displays might also be problematic...

---

### Post by bug67 on 2011-02-16
> **realzippy said:**
> ```
sudo rm /etc/modprobe.d/radeon-kms.conf
```

..makes sure that your displays are controlled by KMS as formerly.
Everything should work as before.If not,then your updates you ran may
cause this.
You should have mentioned that you run a dual display setup;the
xorg.conf should have been modified then.
BTW,compiz with free ATI driver and 2 displays might also be problematic...

Yeah, sorry about not mentioning running two 23" Apple Cinema Displays.  I guess I was just hoping this would be easy somehow.  Thanks for trying to help.

---

### Post by realzippy on 2011-02-17
If you have cleaned up and everything is as it used to be,you could generate
a xorg.conf file on your machine,with both screens running and later on edit the relevant parts.

Press [B]alt+ctrl+F2 (write down/print commands before)
[/B]
log in at opening shell with username & password,type 

```
sudo service gdm stop
```


```
sudo Xorg -configure
```    mind capital "X"


```
startx

```

..now you should have a (large) xorg.conf.new in your home directory.
Post it's content..
edit:
There will be no "harm" by doing this.

---

### Post by bug67 on 2011-02-18
This is going to have to go on hold for the time being.  I have way bigger fish to fry:

[http://ubuntuforums.org/showthread.php?p=10469695#post10469695](http://ubuntuforums.org/showthread.php?p=10469695#post10469695)

---

### Post by bug67 on 2011-02-21
Marked as solved because this machine no longer exists.

---

