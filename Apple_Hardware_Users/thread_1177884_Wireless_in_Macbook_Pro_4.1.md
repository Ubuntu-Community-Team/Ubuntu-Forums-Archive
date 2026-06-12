---
title: "Wireless in Macbook Pro 4.1"
date: 2009-06-03
forum: Apple Hardware Users
---

### Post by tomreid on 2009-06-03
Hi

I have managed to install 9.04 and dual boot Mac and Ubuntu, but I can't get the wireless to work, instructions for this machine are as follows:
***Wireless (Broadcom)***

 ***[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconNIC.png[/IMG] Should work after enabling the proprietary wireless driver in System -> Administration -> Hardware Drivers. You may need to restart the computer in order for the change to take effect. (this is the 'wl' driver provided by Broadcom.) *
*If this is already enabled but your wireless is not working disable it, restart, then enable it and restart again. *
*You can also unload these two modules: **rmmod ssb wl**, and then load only the 'wl' by running: **modprobe wl**. If this works in your case you may want to black list the ssb module. *
[I]The new kernel version 2.6.28-12 seems to disable wireless driver. It does't work neither to unload then reload module nor reinstalling it from System -> Administrator -> Hardware Driver (does not appear any broadcom driver available). At the moment, use old kernel version 2.6.28-11 and it should work after enabling proprietary driver from System -> Administrator -> Hardware Drivers (disable it first, then reboot, then enable it again, reboot).

[/I]Being relatively new to the Linux world, I'm not finding the above easy to understand. I have the hardware driver installed and it seems to be working. I did remove it and re-boot and then activated it again, tried again, but still no wifi. 

I am confused by the references above to "kernel version". I'm running 9.04, is this the new Kernel version? 

The commands * **rmmod ssb wl  ***[B][B]

d[/B][/B][FONT=Arial]**id'nt work**[/FONT][FONT=Arial][B] the terminal said the commands were not possible. 

Can anyone help? The machine is running beautifully, except for the wifi.
[/B][/FONT][I][B][B]
cheers[/B]
[/B][/I]

---

### Post by dman777 on 2009-06-04
check to make sure you are in root.

then, make sure you have those module names correct. you can do a 'lsmod' and it will list them. it may be that they are not even in there. 

Broadcom has it's own closed source driver for linux that works really good. if it works for your model, use it and avoid the tutorial all together. except clean out any modules that could interefere with it. and yes, have the kernel's wifi broadcom disabled. it should be in the repository and you can just install it with rpm.

---

### Post by cyberdork33 on 2009-06-04
doc updated... you want to choose the broadcom STA driver...

---

