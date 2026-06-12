---
title: "intel chipset 965"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by rpzatkof on 2008-01-28
My computer has graphics card -- Intel Express Chipset 965


when I set the card to this on screens and resolutions and log out for it to take effect it freaks out and says that it is running in low resolution mode and I need to reconfigure the screens/graphics


when I go into it it is set to the default again and the most I can get it to is 800x600

---

### Post by rpzatkof on 2008-01-28
anyone think they can help?  i'm stuck on 800x600 :-(

---

### Post by stchman on 2008-01-28
> **rpzatkof said:**
> My computer has graphics card -- Intel Express Chipset 965


when I set the card to this on screens and resolutions and log out for it to take effect it freaks out and says that it is running in low resolution mode and I need to reconfigure the screens/graphics


when I go into it it is set to the default again and the most I can get it to is 800x600

I believe there is a package called xserver-xorg-video-intel

[http://packages.ubuntu.com/gutsy/x11/xserver-xorg-video-intel](http://packages.ubuntu.com/gutsy/x11/xserver-xorg-video-intel)

It is for the i8xx and i9xx video cards.

Just install that package.

```
sudo apt-get install xserver-xorg-video-intel
```

---

### Post by rpzatkof on 2008-01-28
As of now when I try to boot up I get the error


bcm43xx Error: microcode bcm43xx_microcode5.fw not available or load failed

and it wont boot (i'm on a different computer)


what does this mean?

---

### Post by njparton on 2008-01-28
My NAS used to use that chipset without any bother so you have a software issue.

You'll probably need to edit /etc/X11/xorg.conf and manually add higher resolutions to get them to work although ubuntu detected my monitor at 1280x1024 correctly.

---

### Post by rpzatkof on 2008-01-28
> **stchman said:**
> I believe there is a package called xserver-xorg-video-intel

[http://packages.ubuntu.com/gutsy/x11/xserver-xorg-video-intel](http://packages.ubuntu.com/gutsy/x11/xserver-xorg-video-intel)

It is for the i8xx and i9xx video cards.

Just install that package.

```
sudo apt-get install xserver-xorg-video-intel
```


when i type it in it tells me that the package is not available but is referenced in another package (something along those lines) and says that it probably means the package is obsolete

is there anything else?

---

