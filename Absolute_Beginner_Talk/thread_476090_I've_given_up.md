---
title: "I've given up"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Arcturus on 2007-06-16
It's now been three times I've failed attempting to install Ubuntu. It must be my PC hardware. Everything seems like it's going fine, until it's just about to load into the desktop and then I get the seizure type flashing images on my screen. I try going in with safe graphics mode and I just get a blank screen. Ubuntu must be working because I can here the music it plays when you boot in.

These are my computer specs in screenshots below:

[http://f.exoload.com/507/cpu.png](http://f.exoload.com/507/cpu.png)
[http://f.exoload.com/507/cache.png](http://f.exoload.com/507/cache.png)
[http://f.exoload.com/507/mainboard.png](http://f.exoload.com/507/mainboard.png)
[http://f.exoload.com/507/memory.png](http://f.exoload.com/507/memory.png)
[http://f.exoload.com/507/SPD.png](http://f.exoload.com/507/SPD.png)

Also, I never once had this problem when installing the previous version of Ubuntu.

I downloaded InfraRecorder and am burning the ISO with that onto a DVD-R because I've run out of CD-Rs. I've also burnt at 4x speed which is about mid way to maximum speed.

Does anyone have any ideas of what could be going on?

---

### Post by overdrank on 2007-06-16
> **Arcturus said:**
> It's now been three times I've failed attempting to install Ubuntu. It must be my PC hardware. Everything seems like it's going fine, until it's just about to load into the desktop and then I get the seizure type flashing images on my screen. I try going in with safe graphics mode and I just get a blank screen. Ubuntu must be working because I can here the music it plays when you boot in.

These are my computer specs in screenshots below:

[http://f.exoload.com/507/cpu.png](http://f.exoload.com/507/cpu.png)
[http://f.exoload.com/507/cache.png](http://f.exoload.com/507/cache.png)
[http://f.exoload.com/507/mainboard.png](http://f.exoload.com/507/mainboard.png)
[http://f.exoload.com/507/memory.png](http://f.exoload.com/507/memory.png)
[http://f.exoload.com/507/SPD.png](http://f.exoload.com/507/SPD.png)

Also, I never once had this problem when installing the previous version of Ubuntu.

I downloaded InfraRecorder and am burning the ISO with that onto a DVD-R because I've run out of CD-Rs. I've also burnt at 4x speed which is about mid way to maximum speed.

Does anyone have any ideas of what could be going on?

Hi what  video card do you use in your system?:p

---

### Post by Arcturus on 2007-06-16
> **overdrank said:**
> Hi what  video card do you use in your system?:p
nVidia GeForce 5600 FX

---

### Post by deadlikeoscar on 2007-06-16
Are you trying to match your actual video card during installation or are you selecting the vesa driver? I have to go with the vesa driver and then I just use the Restricted Drivers Manager to get my driver after the first boot. I have a GeForce 5500 btw.

---

### Post by Arcturus on 2007-06-16
> **deadlikeoscar said:**
> Are you trying to match your actual video card during installation or are you selecting the vesa driver? I have to go with the vesa driver and then I just use the Restricted Drivers Manager to get my driver after the first boot. I have a GeForce 5500 btw.
I don't understand what you just said. lol

I'm guessing this has something to do with the BIOS? If so, point me in the right direction of what to do and maybe it will work. :shock:

---

### Post by overdrank on 2007-06-16
> **Arcturus said:**
> I don't understand what you just said. lol

I'm guessing this has something to do with the BIOS? If so, point me in the right direction of what to do and maybe it will work. :shock:

Ok so you have not installed ubuntu yet. So have you tried the alternate cd yet? You can try it here
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)
Scroll down to the alternate cd and try that!:popcorn:

---

### Post by deadlikeoscar on 2007-06-16
Sorry I thought you did have it installed. Guess I better rethink that then.

*Edit* Since you said you wanted to just see what it looked like I wouldn't get the alternate install cd until you are ready to install. I never tried it but can you press Ctrl + Alt + F5 and type sudo dpkg-reconfigure xserver-xorg with the live cd? I've never tried it. If it works you can just select the Vesa driver and go with most of the default options.

---

### Post by Arcturus on 2007-06-16
Downloading the alternate CD right now. I wasn't aware of that. Much thanks. :)

Thanks for the help fellas.

---

### Post by Technophobia on 2007-06-16
hit                         CTRL + ALT + F6

log in under your user

type                     vim /etc/X11/xorg.conf

hold the down arrow until you see Section "Device" and under that tell us what driver says.

to quit hit

esc

:     (colon)

q!

---

### Post by Malibu Illusion on 2007-06-16
If when you boot you have access to the command line and network access, you can download the Nvidia drivers directly from their site, install them and modify the xorg.conf automatically with their utility.  You do not need the GUI to do this nor an alternative installation disk.

---

### Post by deadlikeoscar on 2007-06-16
If you do decide to install Ubuntu with your card (Since it is close to mine I will assume anyway) that you should just select the Vesa driver during install (it should make sense when you start) and Ubuntu should load fine. When the desktop comes up, click on System-->Administration-->Restricted Drivers Manager. Then you can activate the Nvidia driver and all should be well.

---

### Post by Arcturus on 2007-06-16
> **deadlikeoscar said:**
> If you do decide to install Ubuntu with your card (Since it is close to mine I will assume anyway) that you should just select the Vesa driver during install (it should make sense when you start) and Ubuntu should load fine. When the desktop comes up, click on System-->Administration-->Restricted Drivers Manager. Then you can activate the Nvidia driver and all should be well.
I will definitely do that. Thanks for the info!

---

### Post by Malibu Illusion on 2007-06-16
Reinstalling like this is like using a nuclear warhead to kill an ant. ^^

---

### Post by deadlikeoscar on 2007-06-17
Why? It was never installed in the first place. The poster was using a live cd and if X couldn't load how could the poster click on the install icon.

---

