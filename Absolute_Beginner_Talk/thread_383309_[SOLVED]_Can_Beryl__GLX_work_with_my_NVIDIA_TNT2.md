---
title: "[SOLVED] Can Beryl / GLX work with my NVIDIA TNT2?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-03-13
Having seen Beryl in action, and having already installed Ubuntu as dual boot with Win XP on my 6 year old Gateway, I'd like to see if I can get Beryl working on that.

My video card is an NVIDIA RIVA TNT2 Model 64.

Looking at the available options in Synaptic, it clearly isn't the nvidia-glx package I should be installing as it's too recent.

So, I downloaded nvidia-glx-legacy (which specifically mentions my card), nvidia-glx-legacy-dev, nvidia-kernel-common, nvidia-settings and nvidia-xconfig. I then (as suggested) ran:

> sudo nvidia-glx-config enable

All good so far! I now get an NVIDIA splash screen and everything still works, so I installed Beryl and ran the key update (I think it's called):

> wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)

And then I did the following instructions that are within the "How to install Beryl/AIGLX (Nvidia)" section on [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

> sudo apt-get install beryl emerald-themes
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
gksudo gedit /etc/X11/xorg.conf
beryl-manager
emerald --replace

But when I run > glxinfo | grep direct, I get:

> Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ": 0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ": 0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0 ".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ": 0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0 ".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ": 0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0 ".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Nothing about direct rendering at all!

I saw another suggestion that I need to enable 3D acceleration on my card, but when I type nvidia-settings there doesn't seem to be this option.

That suggests I've either:

1. Come as far as I can
2. Done something wrong
3. Need to do some more

Can anyone help?!!!

Thanks in advance

---

### Post by overdrank on 2007-03-13
Hi here is a link to supported cards. Hope this helps.
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#nVidia_Cards](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#nVidia_Cards)
good luck!

---

### Post by qprfact on 2007-03-13
Thanks! Mine does seem to be there - it says nVidia TNT2 M64 32MB (tested with kororaa livecd 0.1) - is that different from Ubuntu though? Do I need to install kororaa instead?

---

### Post by chuckyp on 2007-03-13
With the TnT2 cards I believe you need the nvidia-glx-legacy package if you are looking for drivers.  With that installed you should be able to run beryl with out a hitch.

---

### Post by qprfact on 2007-03-13
Yep, I've installed that, and it allows me to access nvidia-settings, but I can't see anything there about 3D acceleration (which I understand I need - is that right?)

So, I think I'm 90% there, but can't quite work out the last bit! Anyone?!

---

### Post by overdrank on 2007-03-13
> **qprfact said:**
> Yep, I've installed that, and it allows me to access nvidia-settings, but I can't see anything there about 3D acceleration (which I understand I need - is that right?)

So, I think I'm 90% there, but can't quite work out the last bit! Anyone?!

Hi I found this link, maybe try it and see where you get.
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)
Hope this helps. good luck!

---

### Post by qprfact on 2007-03-13
Thanks - I'd found this link before, and see this suggests using NVIDIA drivers rather than those within Ubuntu (what I've done so far, in effect) - is this approach more likely to work do you think?

---

### Post by qprfact on 2007-03-14
I was directed by a colleague to this site - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) -
and I followed the instructions.

I then ran ```
glxinfo | grep direct
```

and got the magic answer direct rendering=yes!

So, got much further than I ever have before. 

So, duly installed Beryl. All still good. But no wobbly windows or nice graphic effects, even if I choose Beryl from the Windows Manager option - it keeps reverting back to GNOME.

There's clearly something else that needs to be done - any ideas?!!!

---

### Post by gothica on 2007-06-02
i also have the same problem. is there anyone here that could help us resolve this issue?

---

### Post by rusty4r on 2007-06-02
i had that problem at first, I solved it by searching the beryl forum. I'll see if I can find it for you

---

### Post by gothica on 2007-06-09
thanks man! so have you found it yet?

---

### Post by klabak on 2007-06-12
I have the same problem. Anyone have an answer to this? Thanks.

---

### Post by gothica on 2007-06-15
it would be great if someone can teach us people who have TNT2 cards how to make beryl work. it would be cool to see my 6yr-old PC run 3D desktop ;)

---

### Post by nimitch on 2007-07-17
hi there i have  the  same/similar  problem

some info i found

the legacy 01-7185 nvidia driver does not allow glx with the composite extension
to see if this is your issue check your x log [/var/log/Xorg.0.log] for this error 
 
      (EE) GLX is not supported with the Composite extension 

in your xorg.conf we can either force the issue (apparently unstable) or disable the composite extension

in the device section
```
 Option "AllowGLXWithComposite" "true"
```

the read me has this to say about the above
"Option "AllowGLXWithComposite" "boolean"
Enables GLX even when the Composite X extension is loaded.
ENABLE AT YOUR OWN RISK.  OpenGL applications will not
display correctly in many circumstances with this setting
enabled.  Default: GLX is disabled when Composite is
loaded."

or
at the end of your xorg.conf 

```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```


I went with the allowglxwithcomposite fix. as beryl needs the composite extension
now my glx works but beryl is complaining about GLX_EXT_texture_from_pixmap support..
 I shall go off for another google :-)
.....
one google later 

i did this (DO NOT DO THIS)

I installed the xgl server from the synaptic package manager in an effort to have this extra layer deal with the glx _ext texture_from bitmap
and altered  [/etc/gdm/gdm.conf-custom] by adding this

```
0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

and ended up with a nice black screen with a mouse pointer on it.. at a guess i would say this is the issue with  the xorg.conf  Option "AllowGLXWithComposite" "true"

there is one more avenue to explore using the mesa drivers .. but for today i concede.. at least i can have hardware accelerated gl things..

---

### Post by megamaced on 2007-08-16
I've got Beryl working on an old Geforce2 Ultra, which uses the same LEGACY driver as your TNT2. I downloaded the latest LEGACY 7185 driver from Nvidia's website and followed the instructions [here]("https://help.ubuntu.com/community/NvidiaManual") to get it installed. **HOWEVER** don't comment out DRI like it says to do. Then you need to add Option "AllowGLXWithComposite" "true" into your xorg.conf file as well. For example:

```
Section "Device"
        Identifier      "NVIDIA Corporation NV15BR [GeForce2 Ultra, Bladerunner
        Driver          "nvidia"
        Option          "NoLogo"
        Option          "AllowGLXWithComposite" "true"
        BusID           "PCI:1:0:0"
EndSection
```

That was all I needed to do to get it working with XGL / Beryl. Note that I am on Dapper so have not been able to test with AIGLX. But needless to say it works with XGL.

---

### Post by acorn22 on 2007-08-28
I think I am pretty close too....

Now I am getting this:

```
lowell@minty:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
lowell@minty:~$ 

```

Fesisty Fawn, btw

---

### Post by acorn22 on 2007-09-01
also:

```
lowell@minty:~$ compiz
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
lowell@minty:~$ 


```

I don't really care if it's Beryl or Compiz  or XGL or AIGLX or anything. I just want effects! (and AWN)

---

