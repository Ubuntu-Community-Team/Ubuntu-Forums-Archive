---
title: "[SOLVED] Only the KXStudio logo on restart after installation"
date: 2014-03-12
forum: Any Other OS
---

### Post by Massimo_Morelli on 2014-03-12
Hi guys

I tried to install KXStudio and the installation is  successful, but when I reboot KXStudio logo appears as if he is loading  but nothing happens....

II'm trying to install in SSD.
The  SSD is already prepared for SO installation by GPT formatting and there are two partition. One is for Ubuntu Studio 13.10 which worked  well and the other one would be for KXStudio

I found this guide on an Italian site, but I'm not able to understand what I've to do. I don't understand where I've to give the command that they suggest

this is what the guide says:

```
SSD 

If you have installed KXStudio on an SSD, you may experience frequent stalls early in the boot process to the startup splash screen KXStudio. You can fix this by running: 

     kdesudo kate / etc / default / grub 

Remove the word 'splash' from the options GRUB_CMDLINE_LINUX_DEFAULT, save the file then updated and re-install GRUB using the two commands from the previous section on multi-boot. 

The installer KXStudio does not change the configuration of Solid State Drives for optimum performance. Follow this guide if you want to optimize the performance of your SSD.
```

Someone can help me?

---

