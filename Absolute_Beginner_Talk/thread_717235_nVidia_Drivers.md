---
title: "nVidia Drivers"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Pap3r on 2008-03-06
Hi everyone,

I have been using the nvidia drivers offered by the Restricted Drivers panel for quite some time, and I decided I should try the forceware drivers, just to see how it does.  I installed them earlier, and first off, I got a no screen can be found error.  I had to edit the xorg.conf file and I finally got it working.  However, things are *not* how they were.  

For one thing, when I'm using the "nvidia" drivers, rather than the "nv" drivers, I have to start in Failsafe Gnome for some reason.  I can't enable desktop effects, compiz won't work, my cairo-dock has a solid background, rather than it's nice translucent one prior to the installation, and many other problems.  I can get back to using the old drivers through the Restricted Drivers panel, but I can't enable desktop effects there either.

I only installed them to test it; as I had heard some people say don't bother, and others said you should.  My ui is really ugly now, no eye candy, and I can't play games.  I can't revert back to how it was either.  How do I fix this?

---

### Post by sanddgroper on 2008-03-06
Hi
> only installed them to test it; as I had heard some people say don't bother, and others said you should. My ui is really ugly now, no eye candy, and I can't play games. I can't revert back to how it was either. How do I fix this?
Hmm the saying if it an't F....d dont fix it come to mind.
Reinstalling Ubuntu.?
Try and remove all restricted drivers and start again.

Cheers
Sandy

---

### Post by Pap3r on 2008-03-06
> **sanddgroper said:**
> Hi

Hmm the saying if it an't F....d dont fix it come to mind.
Reinstalling Ubuntu.?
Try and remove all restricted drivers and start again.

Cheers
Sandy

Hehe, I know, I know.. :)

It turns out that installing envy worked, I fixed the install with it, then enabled the restricted drivers and all is well; thank you for the reply though!

---

### Post by Equiflux on 2008-03-06
I recently purchased a 9600 GT and I'm getting the no screen found error as well. How did you edit the config file? Could you give me some detailed info? I'm fairly new to Linux. 

Thanks

---

### Post by Pap3r on 2008-03-06
To edit the file, I just changed the driver listing back to "nv" and started gnome in failsafe.

```
 sudo gedit /etc/X11/xorg.conf 
```

```
Section "Device"
        Identifier      "nVidia Corporation G70 [GeForce 7600 GT]"
        Driver          **"nvidia"**  CHANGE THIS TO "nv"
        Vendorname      "NVIDIA"
        Boardname       "NVIDIA GeForce 7 Series"
        Busid           "PCI:1:0:0"
        Screen  0
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

```
  I then downloaded [Envy]("http://albertomilone.com/nvidia_scripts1.html"), and had it uninstall my old driver.  I then had it reinstall the driver, I restarted my computer and found that it worked; but it didn't load compiz etc.  I went to the Visual Effects (right click desktop -> Change Background -> Visual Effects tab) and hit Custom (May just be Extra for you).  When it prompted me to download/enable the restricted driver I enabled it, and restarted my computer.  

After that, it all worked.  That may have been a bit too messy of an explanation; if you need any more help on it, let me know.  This has happened to me numerous times, but this is the only time I have documented how exactly I solved it.

---

