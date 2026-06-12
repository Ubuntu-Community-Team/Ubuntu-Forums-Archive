---
title: "Should I reinstall 7.10 Yet again or can my install be fixed"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by comfortablynumb on 2007-11-10
I had 7.10 working great just couldn't get the "Visual Effects working" so I Enabled Restricted Nvidia driver reboot, couldn't get my resolution back to 1440x900 even though though my Xorg.conf file was fine, it had 1440x900 listed.  There was just no option in screen resolution or in System | Administration | Screens and Graphics to set the correct screen size.

I unenabled the Restricted driver rebooted, and my resolution was fine again. So I downloaded the latest version of Envy, I let it run and when I rebooted X was broke stating it was running in Safe Graphics mode. When I finally got in it said I had a broken package it showed I had one nvidia kernal and there was another one available that said (gusty) next to it. I was going to force the gusty one but it said that it was going to uninstall my linux kernal, ubuntu restricted and a whole slew of things.

So I just ran Envy and said to uninstall Nvida, rebooted and X was still in safe graphics mode, so I tried to run Envy one more time and still broken package and safe mode ](*,) :-k

Right now X appears Fubar,  the only resolution I can come up with on my own at this point is to reinstall it for a third time. I'm glade I have a separate /home partition,*** but still I don't see why getting Nvidia drivers to work has to be this hard. I have a Geforce II Gts***

If I do reinstall is there an actual way to get Nvida to work or should I just scrap that idea

[B]ECS Mobo Kt266 chipset
Duron 1300
Gefore II GTS AGP
Crucial 512MB DDR
3COM Nic
Soundblaster Live[/B]

---

### Post by matthewcraig on 2007-11-10
You know that Envy is known to mess up your Ubuntu configurations?
Use the Resticted Manager to install binary drivers,

---

### Post by comfortablynumb on 2007-11-10
> **matthewcraig said:**
> You know that Envy is known to mess up your Ubuntu configurations?
Use the Resticted Manager to install binary drivers,

No I didn't know that, well I guess I do now lol...

Thing is when I install the Restricted driver all it does is mess up X. I'm not sure why my screen resolution isn't selectable. If Xorg.conf is configured correctly with 1440x900 then that should allow me to select it.** If I unselect the Restricted driver and reboot then my screen resolution is fine.**

So maybe I just need to install Gusty and say screw getting Nvidia up and running....:lolflag:

---

### Post by bulldog on 2007-11-10
NVidia binary X.Org driver
NVIDIA binary XFree86 4.x/X.Org driver  
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server and support the newer GeForce, nForce and Quadro families of NVIDIA chipsets.
AGP, TV-out and flat panel displays are also supported.
If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy package instead of this one.
To enable the driver, run "sudo nvidia-glx-config enable".

Canonical Ltd. biedt technische ondersteuning en beveiligingsupdates voor NVidia binary X.Org driver
NVidia binary X.Org driver integreert goed in de Ubuntu desktop



I think you should use this driver instead of the newest with envy.
You can find it in add/remove app under the system utillitys.

---

### Post by comfortablynumb on 2007-11-10
Thanks formatting / and reinstalling 7.10 as I type this

---

### Post by comfortablynumb on 2007-11-10
Well back up and running, still debating if I want to try to mess with Nvidia drivers again :/

---

