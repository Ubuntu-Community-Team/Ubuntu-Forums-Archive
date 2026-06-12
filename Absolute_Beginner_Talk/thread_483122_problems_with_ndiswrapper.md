---
title: "problems with ndiswrapper"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by spectrum48k on 2007-06-24
How the heck do I remove installed and alternate wireless card drivers?
I have looked at the tutorial on the ndiswrapper website but nothing works!
The graphical interface for ndiswrapper has stopped working blinks up a blank screen for a split second then dissappears. Is there a simple straight forward system for setting up a belkin F5D700 wireless card?

Thanks

---

### Post by PartisanEntity on 2007-06-24
To remove a driver using ndiswrapper open the terminal and type:

```
sudo ndiswrapper -e *driver*
```

driver = **driver.sys** for example

---

### Post by spectrum48k on 2007-06-24
I managed to delete one of the drivers i didn't want but the alternative driver how do i delete that? thanks

spectrum48k@AMDLINUX:~$ ndiswrapper -e bcm43xx
couldn't delete /etc/ndiswrapper/bcm43xx: No such file or directory
spectrum48k@AMDLINUX:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
spectrum48k@AMDLINUX:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
spectrum48k@AMDLINUX:~$ sudo ndiswrapper -e bcm43xx
couldn't delete /etc/ndiswrapper/bcm43xx: No such file or directory
spectrum48k@AMDLINUX:~$ 


> **PartisanEntity said:**
> To remove a driver using ndiswrapper open the terminal and type:

```
sudo ndiswrapper -e *driver*
```

driver = **driver.sys** for example

---

### Post by PartisanEntity on 2007-06-24
If my memory serves me correctly you cannot delete drivers using ndiswrapper that were not installed through it.

The bcm43xx driver comes with Ubuntu by default I believe, you will have to blacklist it:

Open a Terminal window
Type "sudo gedit /etc/modprobe.d/blacklist"
At the bottom add the lines
#  default kernel drivers
blacklist bcm43xx

You may have to restart for changes to take effect.

---

### Post by spectrum48k on 2007-06-24
Thanks and sorry about my ignorance!
I just tried the blacklist thing, but I don't have write access the blacklist files belongs to 'root'. How do I get write access to blacklist??

> **PartisanEntity said:**
> If my memory serves me correctly you cannot delete drivers using ndiswrapper that were not installed through it.

The bcm43xx driver comes with Ubuntu by default I believe, you will have to blacklist it:

Open a Terminal window
Type "sudo gedit /etc/modprobe.d/blacklist"
At the bottom add the lines
#  default kernel drivers
blacklist bcm43xx

You may have to restart for changes to take effect.

---

### Post by BobCFC on 2007-06-24
if you type sudo before a command it will ask you for a password then do the thing as root such as 

sudo gedit myfile

---

### Post by spectrum48k on 2007-06-24
I did all that but I still get:

bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

> **spectrum48k said:**
> Thanks and sorry about my ignorance!
I just tried the blacklist thing, but I don't have write access the blacklist files belongs to 'root'. How do I get write access to blacklist??

---

### Post by spectrum48k on 2007-06-24
I managed to get the wireless bars icon to come up top right of screen.....does this mean something is working?
none are lit up and 0%!


> **spectrum48k said:**
> I did all that but I still get:

bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

---

### Post by RetepNamenots on 2007-07-04
I'm getting the same problem; tried blacklisting it and everything but I'm still getting (alternate driver: bcm43xx)

---

### Post by Ayuthia on 2007-07-04
Mine still displays that information too, but I still able to use it.  Have you tried using iwlist scan to see if your wireless can see anythiing?

---

