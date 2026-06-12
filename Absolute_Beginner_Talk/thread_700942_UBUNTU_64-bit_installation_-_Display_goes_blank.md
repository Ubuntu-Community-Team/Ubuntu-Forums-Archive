---
title: "UBUNTU 64-bit installation - Display goes blank"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by annyk on 2008-02-18
Hi,

I am a beginner to the world of Ubuntu and desktop Linux.

I faced display related problem while Ubuntu 7.10 installation.

I am running HP dv6000z (windows XP) with AMD Turion64x2 with NVIDIA Geforce display card.
I was planning to make it ubuntu dual-boot. 
I've created a CD with 64-bit desktop version on UBUNTU site.
When I boot this CD and choose default 'start install' option, after initial checks display goes completely blank. I do get bcm43xx microcode related error before display going blank.

System details:
HP dv6000z/ Windows XP SP2/ AMD Tu64x2
NVIDIA GeForce go 6150 display driver

Anybody has any idea what could be wrong here?

I did not try alternate image yet as i ran out of blank DVDs.
But on a sidenote, is there any way to make a bootable USB flash drive and use that for installation instead of liveCD?

Thanks for the help!

-Anny

---

### Post by JoshuaRL on 2008-02-18
There is, but it's a little complicated.

Can you try the option where it uses Low Graphics Mode?  That will use the near-universal vesa driver to install.  After you install, go to the following link and download and run Envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

That should install and configure your video drivers for you correctly.

---

### Post by annyk on 2008-02-19
Hi,

Thanks for the help!

>>>
Can you try the option where it uses Low Graphics Mode? That will use the near-universal vesa driver to install. After you install, go to the following link and download and run Envy:
>>
How do I do that? Do I need to use any advanced option? I remember something like vga=771 option for display issues, but I am not sure how to invoke that option.

thanks again,
Anny

---

### Post by tangibleorange on 2008-02-19
> **annyk said:**
> Hi,

Thanks for the help!

>>>
Can you try the option where it uses Low Graphics Mode? That will use the near-universal vesa driver to install. After you install, go to the following link and download and run Envy:
>>
How do I do that? Do I need to use any advanced option? I remember something like vga=771 option for display issues, but I am not sure how to invoke that option.

thanks again,
Anny

I think what you need to do is try starting in Safe Graphics Mode. On the boot screen, go down to the second option which says "Start Ubuntu on Safe Graphics Mode". As for your kernel option (vga=771), that can be changed once you have installed ubuntu.

---

### Post by annyk on 2008-02-19
> **tangibleorange said:**
> I think what you need to do is try starting in Safe Graphics Mode. On the boot screen, go down to the second option which says "Start Ubuntu on Safe Graphics Mode". As for your kernel option (vga=771), that can be changed once you have installed ubuntu.

Thanks again for the reply!
The safe graphic mode does not work either, I had tried that.

There is an option to Install with driver update CD, I am not sure if it can be used in this case.

regards,
anny

---

### Post by tangibleorange on 2008-02-19
If neither of the options work on the Live CD, I think your only option is the alternate CD, although I know you said this was not possible. Maybe someone else has an idea...

---

### Post by JoshuaRL on 2008-02-19
Alright I have some options for you, but some of them can be a little complicated.  As always, if you have any trouble you can always boot into the LiveCD, load Firefox, and ask questions.

For USB stick installation:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Installation from a Windows partition:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by annyk on 2008-02-22
> **JoshuaRL said:**
> Alright I have some options for you, but some of them can be a little complicated.  As always, if you have any trouble you can always boot into the LiveCD, load Firefox, and ask questions.

For USB stick installation:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Installation from a Windows partition:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

Hi JoshuaRL,

thanks for the links. They are really useful

I could get UBUNTU installed on my laptop by adding 'noapic nolapic' options on command line.
Now next step is to get Broadcom wireless card working, it still seems to have some issues.

-Anny

---

### Post by kooolrock on 2008-02-22
> **annyk said:**
> Hi,

I am a beginner to the world of Ubuntu and desktop Linux.

I faced display related problem while Ubuntu 7.10 installation.

I am running HP dv6000z (windows XP) with AMD Turion64x2 with NVIDIA Geforce display card.
I was planning to make it ubuntu dual-boot. 
I've created a CD with 64-bit desktop version on UBUNTU site.
When I boot this CD and choose default 'start install' option, after initial checks display goes completely blank. I do get bcm43xx microcode related error before display going blank.

System details:
HP dv6000z/ Windows XP SP2/ AMD Tu64x2
NVIDIA GeForce go 6150 display driver

Anybody has any idea what could be wrong here?

I did not try alternate image yet as i ran out of blank DVDs.
But on a sidenote, is there any way to make a bootable USB flash drive and use that for installation instead of liveCD?

Thanks for the help!

-Anny
try "safe graphics mode". I suggest that u visit [COLOR="Blue"][Ubuntu LoCo Team Forums]("http://ubuntuforums.org/forumdisplay.php?f=183")[/COLOR]. take the LIVE help of a fellow Ubunt-ite. It'll be easier to solve ur problem. All the Best!:)

---

### Post by kooolrock on 2008-02-22
> **annyk said:**
> Hi JoshuaRL,

thanks for the links. They are really useful

I could get UBUNTU installed on my laptop by adding 'noapic nolapic' options on command line.
Now next step is to get Broadcom wireless card working, it still seems to have some issues.

-Anny
what exactly is meant by "noapic nolapic"?

---

### Post by JoshuaRL on 2008-02-22
> **kooolrock said:**
> what exactly is meant by "noapic nolapic"?

Those are boot options that can be added and run from the boot page on the CD.  You can see what they are by going into the help menu.

---

