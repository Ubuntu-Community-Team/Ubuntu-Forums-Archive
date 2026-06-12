---
title: "Elgato Hybrid USB TV Tuner Freezes Boot Process"
date: 2008-05-30
forum: Apple Hardware Users
---

### Post by fender177 on 2008-05-30
I've been playing around with my Elgato Hybrid TV Tuner under linux.  I found that the em2880-dvb module is needed in order to use the Hybrid stick (which is actually the Hauppauge HVR-950).  The instructions I used to install the Hybird can be found at: [http://2nrds.com/digital-tv-in-linux-with-em28xx-devices]("http://2nrds.com/digital-tv-in-linux-with-em28xx-devices") (please not, I've also tried the 'experimental' version of the module not listed in the tutorial above with the exact same results). Everything builds just fine, and in fact, I can watch TV just fine.  My problem is rebooting.  

When I reboot the machine (both my iMac and a home built linux box), it hangs on reboot if the TV tuner is plugged in.  I basically have to leave it unplugged and as soon as I am up and running I run *sudo modprobe em2880-dvb* at which time I can plug in the Hybrid just fine.  I've tried adding a file to /etc/modprobe.d to "install" the module into the kernel at boot time, but it does not work.  After reboot, *lsmod |grep em28* shows no signs of having been loaded.  I next tried writing a little script within /etc/rc2.d, which I numbered just lower than the hal script, and also slightly higher than the hal script, neither of which worked.

I believe this issue is leading to other issues, namely LIRC does not want to work either.


Any ideas as to how I can get this module to load before the hardware probes the USB ports and freezes the machine would be great.

Home Built Machine:
Hardy Heron (8.04)
Linux mustang 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux
Intel Core 2 Duo 3.00 GHz
4GB RAM
NVIDIA GeForce 9600 GT Sonic 512MB

iMac 20":
Hardy Heron (8.04)
Linux mustang 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux
Intel Core 2 Duo 2.4GHz
Ati Radeon HD2600 Pro
2GB Ram

---

