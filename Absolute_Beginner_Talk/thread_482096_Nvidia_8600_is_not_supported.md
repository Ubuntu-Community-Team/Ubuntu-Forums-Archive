---
title: "Nvidia 8600 is not supported"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by caseymoore on 2007-06-23
Hey guys, you HAVE to help me.
I recently got a new computer, with a rather new graphics card (NVIDIA 8600). I inserted my fiesty disk into the drive and tried to boot install it. However, when it booted into the live version of fiesty I was greeted with a black screen. I found out that there are linux drivers for it. But how am I supposed to install the drivers when I can't install ubuntu on it?

I'm using windows right now (It's revolting). Nothing works. To get everything to work I'll have to devote a lot of bandwidth. Also, I can't access my 200GB ext3 hard drive. I tried to install this ext3 driver for winxp but it just made explorer freeze. I couldn't find the force quit. I don't think there is one! I'm dying. This is pure torture. I may end my life without linux... Why god... WHY!?!?!?!?!

---

### Post by molly_001 on 2007-06-23
Well I don't know if Ubuntu/Debian is worth all of *that* ... LOL

but ...

Get the LiveCD version of GParted from June, 2006.  Version 2.5-2 .
It will give you a number of *display* options and you will be able
to see what modes (VESA, nVidia, XOrg, etc.) have to be working
together in order to get your screen visible.

Once you have a feel for that,
Try using the Alternate Install CD of Ubuntu 6.06 'Dapper'.
Just try to install that (using text method) and I think
you'll be running up soon.

---

### Post by bodhi.zazen on 2007-06-23
You can install with the alternate CD ...

Then you will need to install the nvidia driver.

This can be done from the command line if X (the gui) fails.

Press Ctrl-Alt-F1 to get to the command line.

Then you can install the nvidia driver with envy :

Here is the home page so you can read it first : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

```
sudo /etc/init.d/gdm stop
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.5-0ubuntu3_all.deb
sudo dpkg -i envy*.deb
sudo envy -t
```

As the nvidia script runs, allow it to configure X (xorg.conf).

The, restart X :
```
sudo /etc/init.d/gdm start
```

Once you are in X you can configure (dual monitors, resolution, etc) with ```
gksudo nvidia-settings
```

---

### Post by caseymoore on 2007-06-23
Thanks, it's nearly working!
I can't make my resolution any higher than 1024x768

---

### Post by bodhi.zazen on 2007-06-23
> **caseymoore said:**
> Thanks, it's nearly working!
I can't make my resolution any higher than 1024x768

What have you done ? What driver are you using ? vesa or nvidia ?

---

### Post by caseymoore on 2007-06-23
Nvidia, I did exactly what you said.

---

### Post by bodhi.zazen on 2007-06-23
Did you run nvidia-settings ?

If so, and no joy, you will need to bring up the issue with nVidia ( I am not sure if your card is supported as it is "new"). Check the Linux drivers.

---

### Post by xl_cheese on 2007-06-23
> **caseymoore said:**
> Thanks, it's nearly working!
I can't make my resolution any higher than 1024x768

You have to manually update your xorg.confg file to get different screen resolutions.

---

### Post by bodhi.zazen on 2007-06-23
> **xl_cheese said:**
> You have to manually update your xorg.confg file to get different screen resolutions.

Not if you run nvidia settings as root (gksudo nvidia-settings) and save the changes.

Cool eh ?

Just keeps getting better :)

---

### Post by Tvinky on 2007-06-28
I got this video card too, and when I wanted to install Ubuntu, it showed me kernel panic with message to start boot with: noapic.
So if you want to install from your CD, put it in, boot and then press F6 and to the end add "noapic" without "". And that's all I have already installed Ubuntu (before 10mins in this way).

But when I searched for restricted drivers, I didn't found anyone, maybe because my PC is new. But I want direct rendering, and tryed to: sudo apt-get install nvidia-glx, but nothig. A tryed sudo dpkg-reconfigure xserver-xorg, but nothing too. Now I'll try it with envy.

P.S If someone got AMD 6000 2x and cat /proc/cpuinfo shows: model name  : AMD Processor model unknown that's ok. Because WinXp/WinVista shows the same. Win & Linux shows what BIOS got there.

Edited: I tryed Envy, and all is ok, my nVidia 8600GT is working:
```

tvinky@ubuntu:~$ glxinfo | grep direct
direct rendering: Yes

```


Thanks all, now I'll know the easiest way :P

Edited (after some time):
OMG, after restart the same sh**! Cant' start X server, and I need to change back nvidia to nv, or again do the same. There are normal solutions? Please answer ;)

---

### Post by aVe-rage on 2007-07-13
Sorry to bump a old topic, but I've got the same problem, my 8600GT only works in the "nv" driver, not the "nvidia" driver; just says there are no screens found when I try using the "nvidia" driver.

Any help?

Oh.. and;

> user@X-Blade:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

And, just in case, heres my xorg.conf; attached. (PS: 32 color depth didn't work.)

---

### Post by Fittersman on 2007-07-14
would the 8600 GT and the 8600 GS (my card) work the same way, and if i followed the previous posts, would my card work?

---

### Post by confused57 on 2007-07-14
> **Fittersman said:**
> would the 8600 GT and the 8600 GS (my card) work the same way, and if i followed the previous posts, would my card work?
You might want to try Method 1 here:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

You'll notice there is a listing of nvidia cards for nvidia-glx-new and nvidia-glx...see if your card is listed here.

Bodhi.zazen also has instructions in this thread for installing the latest Nvidia driver from their website:
[http://ubuntuforums.org/showthread.php?t=495464](http://ubuntuforums.org/showthread.php?t=495464)

---

### Post by xl_cheese on 2007-07-17
I recently had to reinstall the ubuntu os.  I dealt with this card the first time I tried to install the driver.

I updated the kernels to .16 this time before I tried installing the driver.  didn't work. xserver kept breaking.

The only way I could get it to work was booting into the **.15 **kernel and installing via envy.  envy now has the nvidia beta driver as an option.

---

