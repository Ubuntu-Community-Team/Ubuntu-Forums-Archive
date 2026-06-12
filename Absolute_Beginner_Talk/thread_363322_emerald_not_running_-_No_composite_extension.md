---
title: "emerald not running - No composite extension"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-02-16
[on 6.10 - a FRESH install with all updates done, nothing else (except an open gl game to test if open gl worked)]

Going through: 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

I have installed the beta nvidia drivers, and open gl applications work fine. I have installed beryl, but emerald will not load; it keeps having to fall back onto metacity. when run through terminal it says this:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

when i try to select emerald via the beryl icon in the system tray, the topbar flickered and them resumes back to metacity.

I have done this many times before on 6.10, and the same hardware, so I do not know the problem.

I saw the sticky about beryl, and i interpreted it as problems with it (bugs etc), not getting to start, if i'm wrong, and this shouldn't be posted, please let me know (and tell me where I can post it!)

Any help is greatly appreciated :)

thanks in advance...

---

### Post by Waappu on 2007-02-17
Hi

Try re-install / install latest Nvidia driver

download envy and install it
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.6.1-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.6.1-0ubuntu1_all.deb)
press Ctrl+Alt+F1.
Login virtual terminal and type```
envy
```
select install Nvidia driver


Read official howto use envy from here
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

and make sure you have these lines in /etc/X11/xorg.conf
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by moredhel on 2007-02-17
thanks, it had the line

        Option "Composite" "Disable".

I changed to Enable, restarted X11, and it worked again.

Thanks! :D

---

