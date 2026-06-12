---
title: "System Information in Ubuntu 6.10"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by dhavalbbhatt on 2006-11-16
Hi,
I am new to the Linux world and Ubuntu is my first time with any of the Linux distributions. Installing Ubuntu 6.10 was a snap - I have it as a dual boot on my PC. Although, everything seems to be working just fine - there are a couple of things that I need help on.
Screen Resolution - I have scoured the forums and the net and did find a whole bunch of links, however, none have helped so far. My screen is defaulting to 800*640 - whereas on the windows I can get higher resolutions. While it is not something that worries me a lot, but I would still appreciate to use the best possible resolution available for my screen.
Secondly - again not something that hampers me, but would be a nice to know item is - system information, something that I have in Windows, but cannot find in Ubuntu. Is there any application that allows me to see my entire system configuration/hardware in a GUI? I can see my current Ubuntu partition, however, I cannot see the hard drive where the current partition resides (and along with that all other partitions on the hard drive where Ubuntu is installed). I cannot even see the other hard drive that I have in my computer. I have two hard drives - 1 80GB PATA drive and 1 160GB SATA hard drive. I have installed Ubuntu on the SATA hard drive. I would also like to see the video card and sound card information. In a nutshell, I need a GUI application that will allow me to manage my hardware components.

All help is greatly appreciated.

Thanks,
DB

---

### Post by taurus on 2006-11-16
Open a terminal, Applications -> Accessories -> Terminal, 

1.  You probably need to reconfigure your X and then install a driver for your graphic card...

```
sudo dpkg-reconfigure xserver-xorg
```

2.  If you want to see your harddrives, run

```
sudo fdisk -l
```

And if you want a list of your hardware, then run

```
lspci
```

---

### Post by dhavalbbhatt on 2006-11-16
Thanks - that was quick. I will try out those options once I get to my PC tonight.

---

### Post by misha680 on 2006-11-17
Also for system information you can go to System -> Administration -> Device Manager although it can be a little cryptic at times. I think the resolution of the resolution problem (no pun intended :) ) will probably depend on your specific graphics card.

Misha

---

### Post by jonathan21 on 2006-11-17
how do u see memory size and processor speed

---

### Post by misha680 on 2006-11-17
> **jonathan21 said:**
> how do u see memory size and processor speed

Applications->Terminal, then type:

```
cat /proc/cpuinfo
```

and

```
cat /proc/meminfo
```

Misha

---

