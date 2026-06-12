---
title: "X Window System configuration issues"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by sdsoloist on 2007-09-26
When I load Ubuntu, the X Window System fails to load, with the error "Screen(s) found, but none have a usable configuration." I entered sudo dpkg-reconfigure xserver-xorg in Recovery Mode, but I'm not sure what settings to enter. I used my best guess for each entry, but still get the same error. I'm using an HP DV6500 with a GeForce 8400M GS. Is there a way to find the correct settings for this setup?

---

### Post by reckless2k2 on 2007-09-26
did you have a working desktop already and now it doesn't after an update or added something like desktop effects? nvidia drivers?

just need some more details.

---

### Post by st33med on 2007-09-26
Simpler way:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Much simpler.

---

### Post by sdsoloist on 2007-09-26
> **st33med said:**
> Simpler way:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Much simpler.I just tried that an enabled all available resolutions I have, but I'm still getting the same error.

---

### Post by sdsoloist on 2007-09-26
> **reckless2k2 said:**
> did you have a working desktop already and now it doesn't after an update or added something like desktop effects? nvidia drivers?

just need some more details.I'm installing Ubuntu for the first time on my laptop with a Nvidia graphics card.

---

### Post by reckless2k2 on 2007-09-26
try the alternate cd instead of livecd. 

id i miss that? i'm getting my post confused. alternate cd..try it.

---

### Post by sdsoloist on 2007-09-26
I initially tried the live CD, which didn't work, so I spent over 24 hours downloading the DVD image. I don't have any more CDs left, and while I could install another CD image on a DVD, I'd rather try to get this one to work before burning another disk. Most of the settings I have seem to make sense, but I'm not sure how to find the bus identifier.

---

### Post by sdsoloist on 2007-09-28
Is there anything else I should try? I don't want to just go back to Vista but I don't have much choice if this doesn't work.

---

### Post by sdsoloist on 2007-10-01
Last bump before I give up and stick with Vista...

---

### Post by bodhi.zazen on 2007-10-01
We need more information, unless I missed it.

Videocard ?

Monitor ?

Post /ect/X11/xorg.conf

Edit: And there is noting "wrong" with staying with Vista if it fits your needs or until you are comfortable with Ubuntu (I would bet most folks dual boot for a while).

Edit2: Which Nvidia card ??? Have you tried Envy ? [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by sdsoloist on 2007-10-01
As I said in the first post, my video card is an Nvidia GeForce 8400M GS. I'm unsure of how to find out what type of monitor it is, but the computer is an HP DV6500. I am comfortable using Ubuntu, as I had it on my previous desktop, but installation is a whole different story. I can still dual-boot for a while, as you said, but not if I can't even complete the installation.
I have not tried Envy, and I will now. My question regarding Envy is if I am running it from a USB stick, how do I access the files on the USB drive from the command prompt?

---

### Post by bodhi.zazen on 2007-10-01
Oh, sorry I missed that nvidia card.

Yes, I think you need the nvidia driver. I think you need internet access to download the dependencies.

To access your usb card, where is it mounted ? usually in /media

so cd /media/name_of_usb

If it is not auto-mounted,

sudo fdisk -l #this command lists partitions
sudo mkdir /media/usb
sudo mount /dev/sdxy /media/usb #get  'xy' from fdisk

---

