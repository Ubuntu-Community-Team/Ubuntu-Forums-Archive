---
title: "isight macbook 4-1 santarosa Ubuntu 8.10 intrepid"
date: 2009-01-23
forum: Apple Hardware Users
---

### Post by lesage on 2009-01-23
Hello 

I'm installing Ubuntu 8.10 (Intrepid Ibex) on a MacBook (4,1) and I try to get my isight camera working.

To do so I follow the steps on [https://help.ubuntu.com/community/MacBook4-1/Intrepid](https://help.ubuntu.com/community/MacBook4-1/Intrepid)
--------------------------------------------------------------------------
To enable the MacBook's built-in webcam, simply follow these steps:
1. Mount your Mac OS X partition
2. Install the isight-firmware-tools package and direct it to your iSight firmware on the Mac OS X partition (just confirm the default when mounted to /MacOSX)
3. Restart HAL

e.g.:

sudo mkdir /MacOSX && sudo mount /dev/sda2 /MacOSX
sudo aptitude install isight-firmware-tools
sudo invoke-rc.d hal restart
--------------------------------------------------------------------------

All these steps were succesfull but when I test the webcam using cheese or skype I get no image. Both programs recognise the webcam and when I start them the light next to my webcam goes on but there just is no image.. cheese shows the gnome-foot icon and skype just shows a grey rectangle. No error messages whatsoever..
The webcam works fine in macosx and windows xp so it can't be a hardware problem..

Any thoughts anyone?

Thanks a lot,

Lesage

---

### Post by albesan on 2009-01-24
hey,

have you tried running gstreamer-properties on the terminal and selectin the video input on the video tab?

---

### Post by lesage on 2009-01-24
Hi thanks for your reply but just a simple reboot fixed my problem.. for some reason after I rebooted and did nothing else the webcam worked just fine.. (in cheese and skype as well)
I think it's safe to conclude the steps I posted do the trick but I have no explenation for the need to reboot..

anyway I'm happy ;)

thanks for your input

---

### Post by cyberdork33 on 2009-01-24
> **lesage said:**
> Hi thanks for your reply but just a simple reboot fixed my problem.. for some reason after I rebooted and did nothing else the webcam worked just fine.. (in cheese and skype as well)
I think it's safe to conclude the steps I posted do the trick but I have no explenation for the need to reboot..

anyway I'm happy ;)

thanks for your input
I editted the wiki to point to the appropriate documentation. Not only a reboot, but a complete power down and startup is often needed to get this working.

---

### Post by albesan on 2009-01-25
> **lesage said:**
> Hi thanks for your reply but just a simple reboot fixed my problem.. for some reason after I rebooted and did nothing else the webcam worked just fine.. (in cheese and skype as well)
I think it's safe to conclude the steps I posted do the trick but I have no explenation for the need to reboot..

anyway I'm happy ;)

thanks for your input

great.

Mark the thread as solved.

A bit off topic, but are you on intrepid? skype working for you? Is driving me nuts, can't make it work.

---

