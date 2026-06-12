---
title: "Dual Monitors on the ATI All-in-Wonder X800"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by benoflinux on 2008-04-17
Has anyone been able to successfully have dual monitors with two different res in Ubuntu? One of my monitors (main one) is a Dell 2005FPW that I like to have on 1650 x 1050 and a monitor to the right (secondary one), a Dell 2001FP which I like to have at 1600 x 1200. Though Ubuntu, I have not been able to make each of these their respective resolutions. Either one monitor is good, and another is not. Also, I am unable to do dual monitor with two screens without the res on the 2005FPW making me drag around to find the corners of the screen...

Any help would be a appreciated.

(P.S.) .. I've tried to download the newest drivers on ATI (8.4), but keep getting errors.. what the code is encoded with..

Ubuntu 7.10

---

### Post by msmyk2 on 2008-05-13
ATI Radeon X800
I succeeded in setting up dual monitor with different resolutions on Gutsy 7.10. However now I'm trying to do it on Hardy 8.04. 

Try removing the restricted ATI driver via System > Restricted drivers, then install the driver using this instruction:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Cheers

---

### Post by markbuntu on 2008-05-15
If you are running the ati restricted driver have you tried the AMD Catalyst Control Center. amdcccle?
Do you have it?
If not, get it and use that.

---

### Post by Surfrock66 on 2008-06-25
I've followed the guide above completely, and when I reboot after doing aticonfig --initial, it just hangs at a blank screen after the ubuntu loading bar.  I can't do anything until I boot in recovery mode, then reconfigure the X server.  Any next steps?  I've never made this card work before, and it's pissing me off supremely.:(

---

