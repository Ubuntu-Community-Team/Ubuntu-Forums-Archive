---
title: "request: how to for powertop [coretemp]"
date: 2007-06-20
forum: Apple Intel Users
---

### Post by kzm. on 2007-06-20
could anyone please put together a how to install powertop (and may be coretemp) on feisty 7.04 (46bit)?
i am a total noob and i followed the simple instructions on powertop but i only get errors. :(

that would be reaaaaaaallly nice :D

---

### Post by benanzo on 2007-06-21
You need to have a 2.6.21+ kernel in order to use PowerTOP.  That means either [compiling yourself]("http://ubuntuforums.org/showthread.php?t=442941") or using Gutsy.

---

### Post by kzm. on 2007-06-21
thanx for the answer, benanzo. does it make a difference if you wonna have 64bit?
i am kind of scared to compile my own kernel.. the kernel configurator is menus in menus about things i never heard of, so i tried to compile in vmware first and it just hangs there. is that how-to complete would you say? or would you (or anybody) add some steps / comments?

---

### Post by pveith on 2007-06-21
coretemp compile works just like in 32-Bit.

```
sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux mactel-linux
cd mactel-linux/trunk/tools/temperature/
make
sudo modprobe msr
sudo ./coretemp
```

Works ike charm on my 64Bit Ubuntu Feisty.

---

### Post by ivesjd on 2007-06-21
How do you make the msr module load on default?

---

### Post by mdegner on 2007-06-21
Add msr to /etc/modules

> **ivesjd said:**
> How do you make the msr module load on default?

---

### Post by anumbers on 2007-08-12
I've compiled my first kernel so I could use powertop and its been worth it. Right after logging in I use over 25 W but I can cut that almost in half by killing the recommended processes and turning down the brightness. While this has really improved my battery life I can't help but wonder how much better it can get. While idling I get about 200 wakeups per second but the powertop home page says Gnome is capable of only three. I'm new to Ubuntu (I'm still amazed I was able to compile my own kernel (thank you Dirk R. Gently)) so I'm not sure what I need to do to reduce my power consumption. My top causes for wakeup are eth0 and wifi0 which I'm assuming are ethernet and wireless. The thing is these two processes are always near the top regardless of how I'm connecting to the net. They're even running when I'm not connected at all.
So the question is, can I turn this stuff off temporarily or do I need to leave it out when I compile the kernel? Is there any way I can script the wired or wireless connection to sleep after a period of inactivity?
Also, does anyone know if running something other than Gnome (xfce?) will drop my power consumption?

---

### Post by btucker on 2007-08-29
> **pveith said:**
> coretemp compile works just like in 32-Bit.

```
sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux mactel-linux
cd mactel-linux/trunk/tools/temperature/
make
sudo modprobe msr
sudo ./coretemp
```

Works ike charm on my 64Bit Ubuntu Feisty.



The subversion link is now { 29/8 }:
```

svn co https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux mactel-linux

```


Latest powertop is 1.8
```

wget [http://www.linuxpowertop.org/download/powertop-1.8.tar.gz](http://www.linuxpowertop.org/download/powertop-1.8.tar.gz)

```

---

### Post by Gen2ly on 2007-08-29
> **anumbers said:**
>  Is there any way I can script the wired or wireless connection to sleep after a period of inactivity?

I haven't had the chance to try powertop yet but removing the cards module will probably stop its energy usage.

Also a basic script can unload the module:

```
#!/bin/bash

# Toggle Atheros wireless module.

if ifconfig | grep ath0 > /dev/null; then
    rmmod ath_pci; else
    modprobe ath_pci
fi
```

```
chmod +x nameofile
```

Then you'll probably want to save this in /usr/bin

and create a desktop entry like this:

```
  1 [Desktop Entry]
  2 Encoding=UTF-8
  3 Name=Toggle Wifi Card
  4 Exec=nameofile
  5 Icon=logviewer
  6 Terminal=false
  7 Type=Application
  8 StartupNotify=true
  9 Categories=GTK;GNOME;Application;System;
 10  
```

---

