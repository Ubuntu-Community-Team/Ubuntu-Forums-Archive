---
title: "Problem installing nvidia-glx"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-04-25
I would like to have direct rendering but am running into this problem with
both the nvidia-glx and nvidia-glx legacy packages (I have NV5).  After
installing, enabling and rebooting, I get this message on glxinfo and glx
doesn't work at all, e.g. no glxgears, whereas before I got them and they
turned for a while:

```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None]
```

When I remove nvidia-glx and reboot, everything is back to normal.
I noticed that the nvidia driver remains "nv" in xorg.conf throughout
even after I enable nvidia-glx and reboot.  By the way, this is in
Edgy.

Thanks!
M

---

### Post by Nythain on 2007-04-25
reinstall the nvidia-glx drivers, re-enable them, and change the nv to nvidia in your xorg.conf then reboot and try again... nv is the open source driver that ships with ubuntu, so you need to tell x to use the new nvidia drivers

---

### Post by Bachstelze on 2007-04-25
By the way, to "enable" the drivers in Edgy, you do :

```
sudo nvidia-xconfig
```

while in Dapper, you used to do :

```
sudo nvidia-glx-config enable
```

---

### Post by Michl on 2007-04-25
> **HymnToLife said:**
> By the way, to "enable" the drivers in Edgy, you do :

```
sudo nvidia-xconfig
```

while in Dapper, you used to do :

```
sudo nvidia-glx-config enable
```

```
sudo nvidia-xconfig
```

doesn't do anything
```
 sudo: nvidia-xconfig: command not found
```

this is after installing the nvidia-glx legacy drivers.
M

---

### Post by Bachstelze on 2007-04-25
Seems that you still need to do it the "old" way with the legacy drivers...

---

### Post by Michl on 2007-04-26
You are right.  When I installed the new drivers and used
sudo nvidia-xconfig

then it did edit the xorg file.  Unfortunately,
when I rebooted I got that scary screen with the message that there were
problems with the xserver and gdm will not boot, etc. I can;t remember
the error messages in the diagnosis but it was something about the nvidia kernel
numbers not matching.  So I had to go into recovery mode and copy back the old
xorg file.  

Strangely, when I install the legacy drivers and have "nvidia" in the
xorg file, nothing happens except that glx does not work at all
and I have the info given above in glxinfo. But at least I can boot.
I'm not sure what the problem is. 

M

---

### Post by kvonb on 2007-04-26
Don't waste your time or sanity on all that glx guff, just go here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And install "envy", it should solve all your problems :).

---

### Post by maprx on 2007-04-26
> **kvonb said:**
> Don't waste your time or sanity on all that glx guff, just go here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And install "envy", it should solve all your problems :).


tried this, it tells me there are problems with the headers and craps out.  my fiesty has been so unstable since the the final.  I might just start again

---

### Post by Derspankster on 2007-04-26
I'm pretty sure Envy is NOT intended for use with Feisty.

---

### Post by kvonb on 2007-04-26
> **maprx said:**
> tried this, it tells me there are problems with the headers and craps out.  my fiesty has been so unstable since the the final.  I might just start again

Yes, my suggestion was to the original poster, as I believe he/she is running Edgy!

Envy doesn't work on Feisty, I tried it myself ages ago and got the same errors.

I installed the nvidia driver from the nvidia website, it works perfectly for me.

---

### Post by Michl on 2007-04-26
> **kvonb said:**
> Yes, my suggestion was to the original poster, as I believe he/she is running Edgy!


Yes, my question was about a computer running edgy.   Checked the envy site but haven't done the plunge.  I always figure I need to calculate some time for the unforeseen when changing drivers.

I also run fiesty on a computer with an ati radeon 300x or something card, and the ati driver is perfect -- direct rendering, etx.

Michael

---

### Post by kvonb on 2007-04-26
Envy works perfectly for me every time.  I've done several Edgy installations over the Internet for friends, and even installed Beryl remotely.

Envy has never let me down for Edgy!

---

### Post by Michl on 2007-04-26
When I click on the link for the deb package, Firefox gives me a choice to open it with GDebi package installer or to save it to disk.  Is it ok to use this package installer.  Have never used it.  The only none synaptic packages I have installed are Shredder chess and Sun Java for shredder.

Michael

---

### Post by kvonb on 2007-04-26
I normally save it first, then simply click on the downloaded package to install it.  Either way should work I expect :).

Once installed you can run it straight from your system menu, it will download and install all the necessary stuff for you, and I believe you don't even have to reboot anymore!

Pure genuis :).

---

