---
title: "Can't hibernate ubuntu 7.10"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by IK0N on 2008-01-02
I am unable to hibernate my new custom built notebook running Ubuntu Gusty Gibbon 7.10. When I try to hibernate the system the screen goes blank but nothing else, which forces me to do a restart by pushing the power button. I'm not sure what to do next please help.

Specs on the machine
MSI MS-171A86-002
ATI Radeon HD 2600 (ATI Radeon M76 512MB)
AMD TURION 64 X2 TL-66
Kingston KVR667D2S5/2G R
Intel Wireless WiFi Link 4965AGN
Western Digital HD-WD2500BEVS (triple boot of Windows Vista Business 64-bit, Fedora core 8 64-bit, Ubuntu Gusty Gibbon 64-bit)
Sorry I was thinking about when I first built the machine now the specs are accurate.

---

### Post by LaRoza on 2008-01-02
Hibernating with Ubuntu isn't all that great yet. I know of no fix, other than not doing it. Hopefully, it will be fixed in the future.

---

### Post by snakeeyes on 2008-01-02
For any Linux system it would always have been better if u used an Nvidia card, are u using Gutsy or Hardy cause at the bottom ur specs say Hardy. Does hibernate work in Fedora?

---

### Post by IK0N on 2008-01-02
No fedora is also unable to hibernate. I guess I have no choice but to wait.

---

### Post by LowSky on 2008-01-02
this might help. its for Fiesty but its worth a shot
[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

```
sudo apt-get install uswsusp
sudo s2disk        ## CAUTION: make sure data is saved for this test!

```

---

### Post by snakeeyes on 2008-01-02
> **IK0N said:**
> No fedora is also unable to hibernate. I guess I have no choice but to wait.
You still didn't answer which version of Ubuntu u were using, Gutsy or Hardy. I also suggest that u download the latest ATI drivers from their website. Do u have any other onboard vga card or does ur system only have an ATI card? That will help us as well?

Another thing to tell us is which wireless card u use cause its drivers may interrupt the hibernate process. Also install kpowersave, it gives u more control over suspend to ram and disk.

sudo apt-get install kpowersave

---

### Post by IK0N on 2008-01-02
> **snakeeyes said:**
> You still didn't answer which version of Ubuntu u were using, Gutsy or Hardy. I also suggest that u download the latest ATI drivers from their website. Do u have any other onboard vga card or does ur system only have an ATI card? That will help us as well?

Another thing to tell us is which wireless card u use cause its drivers may interrupt the hibernate process. Also install kpowersave, it gives u more control over suspend to ram and disk.

sudo apt-get install kpowersave

Lowsky I tried the command and it was a no go the system just had a blank screen causing me to do a force restart.

I have Gusty Gibbon. Hardy was a typo. I used envy to get the lateset drivers from AMD. My notebook only has the ATI Radeon HD 2600 (ATI Radeon M76 512MB). I'm using Intel Wireless WiFi Link 4965AGN; the card is not installed at this time so it is not a cause.

---

### Post by snakeeyes on 2008-01-02
In Gutsy u r probably using kernel 2.6.22-14 right? There was a bug report it broke suspend and hibernate on many laptops and Macbooks. R u using Beryl or Compiz Fusion as well?

Can u check the kernel version again on Ubuntu and Fedora please, go to terminal or konsole and type:

"uname -r"

Also try suspend to ram and disk with 3d effects off. Also try installing kpowersave as well as it gives error messages if something fails to want to go to suspend.

"sudo apt-get install kpowersave"

---

### Post by dimbulb1024 on 2008-01-02
Just a shot in the dark, what is your swap file size. I had issues until I figured out my swap file was to small. I have 2GB of memory so I set my swap file to 500mb and I found out it was to small for Hybernate.

---

### Post by IK0N on 2008-01-03
> **snakeeyes said:**
> In Gutsy u r probably using kernel 2.6.22-14 right? There was a bug report it broke suspend and hibernate on many laptops and Macbooks. R u using Beryl or Compiz Fusion as well?

Can u check the kernel version again on Ubuntu and Fedora please, go to terminal or konsole and type:

"uname -r"

Also try suspend to ram and disk with 3d effects off. Also try installing kpowersave as well as it gives error messages if something fails to want to go to suspend.

"sudo apt-get install kpowersave"

Kernel 2.6.22-14-generic.
I'm running compiz/compizconfig setting manager w/ the mac interface.
I've already tried kpowersave it never worked for me.

---

### Post by IK0N on 2008-01-03
> **dimbulb1024 said:**
> Just a shot in the dark, what is your swap file size. I had issues until I figured out my swap file was to small. I have 2GB of memory so I set my swap file to 500mb and I found out it was to small for Hybernate.

I have 4GB of ram installed in my notebook so I made a swap of 8GB

---

