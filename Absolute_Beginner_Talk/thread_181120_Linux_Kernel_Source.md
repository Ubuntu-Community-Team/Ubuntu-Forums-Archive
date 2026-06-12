---
title: "Linux Kernel Source"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-05-23
Trying to compile a RT2500 driver for the PCI card from ralinktech.com. When I follow the README (make config) it says:
[B]
-------------------- Ralink RT2500 Station Configuration --------------------

  Linux kernel source directory [/usr/src/linux-2.6.15-23-386]: usr/src/linux-headers-2.6.15-23

Linux source tree 'usr/src/linux-headers-2.6.15-23' is incomplete or missing!

Configuration failed

make: *** [config] Error 1
[/B]
I've already downloaded my Kernel headers aswell and the path to the Kernel Headers folder is correct. 

I'm baffled :S Any Ideas?

---

### Post by 23meg on 2006-05-23
Did you install the related linux-source package? Type ```
apt-cache search linux-source
```to find the appropriate source package for your current kernel and install it.

---

### Post by tartarian on 2006-05-23
When I type that into the kernel it outputs this:

linux-source - Linux kernel source with Ubuntu patches
linux-source-2.6.15 - Linux kernel source for version 2.6.15 with Ubuntu patches

So I run a Synaptic search for linux-source-2.6.15 right?

---

### Post by 23meg on 2006-05-23
Install the latter package. ```
sudo apt-get install linux-source-2.6.15
```

---

### Post by skippy81 on 2006-05-23
I am using a newer kernel to you, but I have a driver called rt2500.ko allready as part of my kernel package.  Why don't you see if you have it allready too?

Open a terminal and type:

> sudo modprobe rt2500

You never know, it might be your day :D

---

### Post by tartarian on 2006-05-23
Its never my lucky day..... unless that's meant to do nothing? It just goes onto a new  line with oliver@ubuntu:~$ on. Thinking thats not meant to happen? 
Thankyou anyway!!! :D

---

### Post by skippy81 on 2006-05-23
That is meant to happen.  If the module didnt exist then this would have happened:

> skippy@ubuntu:~$ sudo modprobe chucknorris
Password:
FATAL: Module chucknorris not found.
skippy@ubuntu:~$


You can see which modules are loaded with:

> lsmod

A list of loaded kernel modules will be printed out.  You should see rt2500 on that list.  If it is then congratulations, you have saved yourself compiling the module.  

As for setting up a wireless connection, im afraid my knowledge is kinda weak here. 

> ifconfig and > iwconfig are good commands to start with.  You may even be able to adjust it under "System>Admin>Network" menu.

---

### Post by 23meg on 2006-05-23
Type ```
lsmod |grep rt2500
``` If nothing comes up and you just get another prompt, you don't have the module in your kernel.

---

### Post by az on 2006-05-23
[QUOTE=23meg] find the appropriate source package for your current kernel and install it.[/QUOTE]
That will be pretty useless unless you then unpack the kernel bzip archive, config it to match your running kernel and then compile it.  You do not end up with a useable linux-tree by installing the linux-source packages.

Use the linux-headers instead.  If theyare not working for you, you do not have the neccessary toolchain installed, or the original source is not properly packaged.

In this case,

"Linux source tree 'usr/src/linux-headers-2.6.15-23' is incomplete or missing!"
should be

Linux source tree '/usr/src/linux-headers-2.6.15-23' is incomplete or missing!
(missing /)

---

### Post by tartarian on 2006-05-23
Ok.... lot of information here! thanks guys! 

oliver@ubuntu:/$ lsmod | grep rt2500
rt2500                175844  1

Does this mean that I already have the driver?? Have I just wasted the last few days of my life? :D 

So thats one piece of the wireless puzzle destroyed, where do you think I should go from here if I have the driver for my chip but it still doesnt work??

THANKYOU!

---

### Post by skippy81 on 2006-05-23
Your module is definately loaded.  However, a wireless card requires more than just a driver, it needs to be configured to pick up on the right network etc.  Also bear in mind that if your wireless network is encrypted you will need to share the encryption key with your linux machine. 

I just found these, they might be helpful:

> [https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)

> [https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29)

Oh and just to help you out, if one of the guides tells you to edit a file you need to use the command > sudo gedit followed by the path and file name.

---

