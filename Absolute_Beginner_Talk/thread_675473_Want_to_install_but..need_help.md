---
title: "Want to install but..need help"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Dunover on 2008-01-22
Hi
on My husband computer,  I can boot 7.10 only in safe graphics mode, and it appear to be fine.... with out that mode the system hangs or takes forever to boot.

Did put in a 6.06 version, boots fast but only has a 640 X 480 resolution with no option to change
this is the system info

ECS RS400-a mb  2.33 athlon processor
1GB ram
Onboard graphics is ati radeon express 200

I do have a ATI Radeon 64 MB DDr 7000graphics card that I could put in? 

What is the best way to install ubuntu? I prefer to install 7.10, but want a good system? 
Thanks!
Corisa

---

### Post by A4006 on 2008-01-22
Your system looks like it would be more than able to run Ubuntu 7.10 normally.  You might want to try the alternate install CD that uses a text-based installer.  The live CD uses about two times more of your system resources than the installed version, which could be causing your problems (although I've used the Live CD on a system with 512 MB of RAM, a 700 MHz processor, and 4 MB of video memory).  If all else fails you could try a derivative of Ubuntu that uses less resources like Xubuntu.

---

### Post by dstew on 2008-01-22
> Onboard graphics is ati radeon express 200To get the display to work well you need to install ATI restricted driver. There is the fgrlx driver in Synaptic. Also, the [Envy]("http://albertomilone.com/nvidia_scripts1.html") script is recommended by many.

---

### Post by A4006 on 2008-01-22
Why don't you just install your ATI Radeon card and see if Ubuntu boots without having to boot it in safe graphics mode.

---

### Post by Dunover on 2008-01-22
> To get the display to work well you need to install ATI restricted driver. There is the fgrlx driver in Synaptic. Also, the Envy script is recommended by many.

Thanks for that info.... is that for the 7.10 version?  And since you are talking greek to me where would I go to get those drivers and which one is the safest?

Thanks!
COrisa

---

### Post by A4006 on 2008-01-22
I'm partial to Envy, because of it's nice large buttons and easy driver installation.

---

### Post by Dunover on 2008-01-22
ok what version is "envy" ??

cori

---

### Post by A4006 on 2008-01-22
Envy is the software tool to install the driver, not the driver itself.  Download the file here [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu1_all.deb]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu1_all.deb") and install it (it is a .deb file, so you can just select "Open with GDebi Package Installer") once installed, you will see it under Applications>>System Tools>>Envy.  It might ask you to install some additional packages - this is normal.  Just select "Install ATI drivers" and you're good to go.  BTW it does take a while to download, install and configure everything, so be patient.

---

