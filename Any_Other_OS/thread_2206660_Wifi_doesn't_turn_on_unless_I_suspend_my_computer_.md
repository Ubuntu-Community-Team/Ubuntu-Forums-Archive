---
title: "Wifi doesn't turn on unless I suspend my computer first."
date: 2014-02-20
forum: Any Other OS
---

### Post by Garchomps on 2014-02-20
I have tried the following commands to fix this and neither works.
```
ip link set phy0 up
nmcli nm wifi on
```
Whereas the latter would once work. This problem is with every distro I run. My wifi card is a Intel Corporation Centrino Wireless-N 2230. I need this because I'd like to run Steam at startup. How do I make it so my wireless card activates at boot without having to suspend it first? Thank you in advance for anyone who attemempts to answer :P

---

### Post by varunendra on 2014-02-20
Let's see whatever we can do with it. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Garchomps on 2014-02-20
Here you go, hope it helps.

---

### Post by varunendra on 2014-02-20
So you are using Manjaro, not Ubuntu.

I don't know about Manjaro, but from the report it seems either it is very different from Ubuntu in terms of networking, or is broken is some ways.

I'm not sure I can help with that, but I'll try if you are sure it is functioning normally and is not broken. On the other hand, I may be able to help better with Ubuntu, of course unless you have any certain advantage with Manjaro and wish to stick with it.

In any case, having (apparently) incomplete configuration entries in Network Manager configuration files, and having no /etc/network/interfaces file (or a blank one) doesn't look right to me. Can you boot with its Live CD/DVD and post the script report from there? So that I can see if the Live session has same settings - which may help us deciding whether the current report is normal or is your installation broken in some ways.

Lastly, it seems you used a USB wireless adapter as well. Was it plugged in when you booted? Try booting without it being plugged in, and see if the native wireless works without suspending.

---

### Post by papibe on 2014-02-20
Thread moved to **Other OS/Distro Support**.

---

### Post by Bucky Ball on 2014-02-21
Try here:

[http://forum.manjaro.org/](http://forum.manjaro.org/)

---

### Post by Garchomps on 2014-02-21
I don't see why this is in the other os section considering this effects every distro I run including Ubuntu, but oh well. I ran it on the live CD, the results were the same. However, before being suspended phy0 is the only listed wireless network interface whereas after being suspended it lists both that and the blutooth's interface (using rfkill). That's all the information I could give. Althoughm the only time I ran Ubuntu it was off a netinstall so I'm not 100% sure I'd get the same results with a standard one.

---

### Post by varunendra on 2014-02-21
> **Garchomps said:**
> I don't see why this is in the other os section considering this effects every distro I run including Ubuntu

Because you are CURRENTLY NOT using Ubuntu, and the report shows that the network configuration is VERY different from normal Ubuntu installation. As such, the regular Ubuntu users like me may not be able to help you the same way as we can with Ubuntu.

Please post back the report you generated from the live session. You can copy the file to a USB drive or a hard disk partition and attach it in your next post.

---

### Post by Bucky Ball on 2014-02-21
> **varunendra said:**
> Because you are CURRENTLY NOT using Ubuntu, and the report shows that the network configuration is VERY different from normal Ubuntu installation.

^^^
This.

---

### Post by Garchomps on 2014-02-22
I have determined it is because linux does recognize my laptop keyboard's wifi on/off key. If there is any way to enable this please let me know.

---

### Post by papibe on 2014-02-22
Hi Garchomps.

Have you tried looking into the BIOS if there's an option to turn it on there?

Regards.

---

### Post by rjt69 on 2014-02-28
From a terminal, enter "```
udevadm monitor
```" then press  some Fn keys that work and do not work, such as the rfkill button.

If your system has hal, try the ```
lshal
``` command.

i would also look at** ```
/usr/share/doc/udev-*/README.keymap.txt
```** for details on enumerating "broken" keys and getting them submitted upstream.

With the udev ```
**README.keymap.txt**
``` and the directory ```
**/etc/udev/rules.d/**
```, there should be some way to add a file here to set your own rule for calling rfkill on or off.

You need to enable it to get a dynamic config:

```
ip link set wlan0 up
ip link set wlan0 dynamic on
```

---

