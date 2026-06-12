---
title: "CD Burner not recognized"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by ch1ck3n on 2006-07-08
I am having issues with my CD Burner not being recognized. I have 2 separate drives, one is a CD-ROM and one is an Acer 24X10X40 Burner which is hooked up  to the Drive 1 ribbon and P3 plug on the inside of the computer (if that helps).
The CD-ROM is recognized fine, but the Burner is not. When I try to open Serpentine, i get this Error message:

'No recording drive found on your system, therefore some of Serpentine's functionalities will be disabled.'

When I just looked at my burner I noticed there are 2 LEDs on the front of it, one labeled Disc In and the other labeled Waiting. The 'Waiting' LED is on (solid red). If I hit the button to open the drive, it will not open.

Here is the output of my typing mount into the terminal:

```

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-25-386/volatile type tmpfs (rw)

```

So, How can I get my CD Burner recognized so that I will be able to burn CDs?

I probably provided too much information here, but i'm just trying to make it as easy for you guys as possible. 

This computer is a Compaq 5WV271 desktop. (fairly old)

Thanks

---

### Post by Arisna on 2006-07-08
Have you done hardware work with this computer recently?  It sounds to me like the IDE ribbon cable might be in backward in the burner.

---

### Post by ch1ck3n on 2006-07-08
> **Arisna said:**
> Have you done hardware work with this computer recently?  It sounds to me like the IDE ribbon cable might be in backward in the burner.

I just had the box open today, it seemed fine to me.

---

