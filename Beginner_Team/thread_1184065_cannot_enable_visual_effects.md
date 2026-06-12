---
title: "cannot enable visual effects?"
date: 2009-06-10
forum: Beginner Team
---

### Post by dineshrathod2216 on 2009-06-10
Hi i m Dinesh. I just installed ubuntu 9.04 on my compaq laptop today and i m a complete newbie to ubuntu. So please be patient. 
When i click on System>Preferences>Appearance>Visual Effects, its set to **NONE. **I m unable to change it to **Normal**. It tries to search for drivers then gives this error, "visual effects could not be enabled". 

Please help,
Thanks,
Dinesh.

---

### Post by doas777 on 2009-06-10
> **dineshrathod2216 said:**
> Hi i m Dinesh. I just installed ubuntu 9.04 on my compaq laptop today and i m a complete newbie to ubuntu. So please be patient. 
When i click on System>Preferences>Appearance>Visual Effects, its set to **NONE. **I m unable to change it to **Normal**. It tries to search for drivers then gives this error, "visual effects could not be enabled". 

Please help,
Thanks,
Dinesh.

what kind of vid card do you have? have you installed the restricted driver?
you can find out your card type, by opening a terminal (applications -> accessories) and pasting in:
```
sudo lshw -C display
```

while you are in the terminal, also run this command:
```
sudo apt-get update
```

this command will update the repository lists on your PC, including new packages. after updating it, any restricted drivers for your device should be detected, and a message will appear in your notification area, indicating that new hardware drivers are available.

---

### Post by dineshrathod2216 on 2009-06-10
Its a compaq laptop and the motherboard is Intel 965M so i have inbuild video memory of aroung 512 MB.

---

### Post by doas777 on 2009-06-10
I don't use intel, so I can only give so much advice, but  the intel 3d driver is called xserver-xorg-video-intel and you can install it manually at the terminal with:

```
sudo apt-get install xserver-xorg-video-intel
```

after that, reboot, and see.

if your graphics are all messed up afterward, reboot, and when it's just getting started, enter the grub menu (press escape when it tells you to). select recovery mode. then select root terminal. then enter this command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to disable the driver new driver and reinstall the generic one.

---

### Post by dineshrathod2216 on 2009-06-10
hi i ran the above command and it gave me this : 
*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
Did this help?

---

### Post by dineshrathod2216 on 2009-06-10
i also tried to update the repo and it gave me an update for my wireless driver.

---

