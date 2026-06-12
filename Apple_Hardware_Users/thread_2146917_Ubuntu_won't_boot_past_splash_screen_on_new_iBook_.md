---
title: "Ubuntu won't boot past splash screen on new iBook G4 install"
date: 2013-05-20
forum: Apple Hardware Users
---

### Post by hollywoodpete on 2013-05-20
I have been trying to install Ubuntu 12.04 PowerPC on an iBook G4. The install appears to go fine but on booting into the new OS the screen gets to the Splash screen where is says Ubuntu 12.04 with four dots below but it also give an error message  [   25.979435] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found. 

It says to go to a website and download the firmware. Unfortunately the screen and all of the keys are locked. Reboot doesn't help. Any help would be appreciated.

---

### Post by michiganmac on 2013-05-20
> **hollywoodpete said:**
> I have been trying to install Ubuntu 12.04 PowerPC on an iBook G4. The install appears to go fine but on booting into the new OS the screen gets to the Splash screen where is says Ubuntu 12.04 with four dots below but it also give an error message  [   25.979435] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found. 

It says to go to a website and download the firmware. Unfortunately the screen and all of the keys are locked. Reboot doesn't help. Any help would be appreciated.

Hi! This is a known bug with a workaround that can be found on this page in the wiki:

[https://wiki.ubuntu.com/PowerPCKnownIssues#A12.04_Precise_Pangolin](https://wiki.ubuntu.com/PowerPCKnownIssues#A12.04_Precise_Pangolin)

Scroll down the page to the heading "b43 (Airport Extreme) hangs at missing firmware", and follow the directions. If you already have the system installed, then you want to use the second line, "[COLOR=#333333]Linux b43.blacklist=yes" at the boot: prompt. Then, after your system finishes booting, you can follow the directions to install the missing firmware.[/COLOR]

I had the same issue when I installed Lubuntu 12.04 on my iBook G4, 1.33 GHz machine. Depending on which iBook G4 you have, there will probably be some more useful information on this page you will need, like how to get your sound to work.
[B][COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR][/B][COLOR=#222222][FONT=Verdana]Good luck, and please report back here your success![/FONT][/COLOR]

---

