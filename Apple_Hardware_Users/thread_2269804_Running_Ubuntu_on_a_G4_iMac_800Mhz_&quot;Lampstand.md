---
title: "Running Ubuntu on a G4 iMac 800Mhz &quot;Lampstand&quot;"
date: 2015-03-18
forum: Apple Hardware Users
---

### Post by Jon Bradbury on 2015-03-18
Hi

I am trying to install a recent PPC Ubuntu distribution on a 15" G4 iMac 800Mhz "lampstand" model (lubuntu 14.10, but this applies to other 14.x *ubuntus) and I have done a bit of searching about.


I was successful in installing using the "alternative installation disk" but I have to jump through several hoops to get to the desktop. The following seems to work on my machine (which has NVIDIA N11 GEForce2 MX/MX 400 card):

At yaboot prompt, type
```

Linux video=offb:off nouveau.modeset=0 single

```

Wait for disk activity to cease (screen shows no activity) / boot to complete, then enter blind:
```

modprobe nvidiafb mode_option=1024x768-16

```

On hitting return I see the command prompt. I then start the display manager:
```

start lightdm

```

..and I get a greeting / login window. Thereafter the desktop works properly.

My question is, how can I configure the yaboot and modprobe steps to happen automatically every bootup (and removing the single user mode boot parameter so that the machine boots straight to the lightdm greeter / login screen)?

Thanks
JonB

---

### Post by Jon Bradbury on 2015-03-18
Ok, I think I can answer my own question after some more scouting about:

1. Update /etc/yaboot.conf. at the end of each image block, add the line
```
append="quiet splash video=offb:off nomodeset"
```

You can probably drop the quiet / splash bits.

2. Issue the command
```
sudo ybin -v -C /etc/yaboot.conf
```

This updates the yaboot menu by applying the content of the /etc/yaboot.conf.

3. Append nvidiafb driver to /etc/modules file (used to tell the kernel what modules to load at boot time):
```
nvidiafb mode_option=1024x768-16
``` 

4. Job's a good 'un. Reboot.

---

### Post by slickymaster on 2015-03-18
*Moved to the ***Apple Hardware Users*** sub-forum*

---

### Post by este.el.paz on 2015-03-18
@jon:

There are a number of threads here about getting "12.04 on iMac 800 PPC" with loads of details.  You will probably need to set up an xorg.conf file and get the video module set up there with even horz/vert refresh rates mentioned.  It's a bit involved, but I managed to do it on my now defunct iMac 800, the fbdev module was just fine, but the "nv" driver was better . . . hard to find that nv driver now I believe.

e...

---

### Post by Jon Bradbury on 2015-03-19
The technique I documented came from various sources and seems to work OK. Uses nvidiafb driver. No need to dip into org.conf (sorry to ask, but is this even supported these days? I can never find it... Guess I'll have to google some more).

I like the iLamp with Ubuntu MATE, it's quite lovely. Nice to know it runs pretty well too, even if it is difficult to install.

Cheers
JonB

---

