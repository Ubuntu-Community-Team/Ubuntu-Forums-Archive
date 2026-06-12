---
title: "Nvidia 32 Bit Colour ??"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Copyright on 2007-08-28
Hey guys,

Just switched over to Ubuntu on my laptop from Vista, I've got most things going however upon running nvidia-settings I find that my computer is running in 16 bit colour.  When i try to switch to 32 bit in the X Screen I'am told that I cannot apply due to problems with X screen.

I'am running a Geforce GO 7600 with latest drivers.

Cheers,
Copyright

---

### Post by insane_alien on 2007-08-28
try 24-bit colour. 32-bit colour technically doesn't exist. 32-bit is 24-bit colour with an alpha channel.

---

### Post by Copyright on 2007-08-28
There is no option for 24 bit colour however, by going into the xorg.conf would changing colour_depth or bit_depth (cant remember what its called as I'm reformatting my ubuntu machine atm) and changing it to 24 bit do the job?

Cheers

---

### Post by phb5 on 2007-08-28
I use same GPU and it worked for me! :)

---

### Post by Copyright on 2007-08-28
> **phb5 said:**
> I use same GPU and it worked for me! :)

You just changed the bit_depth or colou_ depth in the xorg.conf file to 24?  Did you use terminal or just edit the actual file, because when editing the actual file it was like 8 different settings for the same resolution (I'm guessing its the top one you edit) however I'm a bit thingy editing it after changing it to 32 only to find on rebooting the X server could not be loaded.

---

### Post by bodhi.zazen on 2007-08-28
If you get this error message :

> No GLXFBConfig for depth 32

		Put this in the "Screen" section of /etc/x11/xorg.conf :
> 		Option "AddARGBGLXVisuals" "True"
		Option "DisableGLXRootClipping" "True"

---

### Post by phb5 on 2007-08-28
> **Copyright said:**
> You just changed the bit_depth or colou_ depth in the xorg.conf file to 24?
Yes!

here's part of my xorg.conf:
```

    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce Go 7600]"
    Monitor        "Generic Monitor"
    [COLOR="Red"]DefaultDepth    24[/COLOR]
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"

```

I changed it manually.
to edit xorg.conf you'll have to be root

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Steveway on 2007-08-28
That last command is wrong!
The right one would be:
gksu gedit /etc/X11/xorg.conf

---

### Post by phb5 on 2007-08-28
> **Steveway said:**
> That last command is wrong!
The right one would be:
gksu gedit /etc/X11/xorg.conf

works in both ways. at least for me.

---

### Post by SoloSalsa on 2007-08-28
> **insane_alien said:**
> 32-bit colour technically doesn't exist. 32-bit is 24-bit colour with an alpha channel.
I know this is true in transparent graphics, but why does this term exist for screens?  There is no alpha in video output that I know of...
Also, why, then, is there sixteen bit?  Is it not twelve bit?

---

### Post by Steveway on 2007-08-28
Yes it works but you should definatly use gksu for graphical applications.
Using sudo can make some problems, something with the .ICEauthority file or so.

---

### Post by Kryten107 on 2007-08-28
> **phb5 said:**
> works in both ways. at least for me.

Technically it works but when running a graphical program like GEdit from the command line with root access, use gksu instead of sudo. It's safer, no risk of screwing things up.

Don't ask me how, I just know that's what you're supposed to do. sudo for CLI stuff, gksu for GUI stuff.

---

### Post by bodhi.zazen on 2007-08-29
LOL

usualluy sudo is OK for graphical apps, but rarely it will be problematic so yes gksu is prefered (or kdesu for KDE/Kubuntu).

For a nice overview of the issues see this link : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Steveway on 2007-08-29
> usualluy sudo is OK for graphical apps, but rarely it will be problematic so yes gksu is prefered (or kedsu for KDE/Kubuntu).
You mean kdesu, don't you? Just a typo but you're right with everything else.

---

### Post by BrendaEM on 2008-02-01
I've been bitten my this issue running an application under Wine. The fix posted does not fool the application into thinking that it has a 32-bit Windows screen.

---

### Post by r4ik on 2008-02-01
Beautiful it also pushes my glxgears thanks !

---

