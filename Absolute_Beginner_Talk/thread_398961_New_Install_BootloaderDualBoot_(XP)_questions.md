---
title: "New Install Bootloader/DualBoot (XP) questions"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Mantis2600 on 2007-04-01
Hello everyone, I'm new to the community and I'm attempting to participate in a "week of Ubuntu" immersion to allow myself to learn the architecture and not be tempted to go back to windows "because it's easier." 


 I've got a bit of experience with Kubuntu (6.06 LTS) and here's my question:  The last time I installed for dual boot, everything went fine, but the Bootlader would boot into Linux after five seconds automatically.  Is there a way to change this easily?  I'd like to have a bit of control over this, especially while I'm in the installation faze and will be switching to windows more frequently then I'll be using kubuntu.


Thanks!

---

### Post by mac.ryan on 2007-04-01
You can edit all the parameters of grub from within the file /boot/grub/menu.lst the file is quite self-explenatory... however the parameter is called "timeout", the units are seconds. You can also change the default system to windows, if you prefer.


To edit that file from command line:
```
sudo nano /boot/grub/menu.lst
```

---

