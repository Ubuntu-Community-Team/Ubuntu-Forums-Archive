---
title: "[SOLVED] Cannot Exit GDM X-Server"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-21
I need to install the 9755 NVIDIA driver for this onbaord sound card I have, but I cannot get the xserver to stop running.  Driver found here....
[http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)


In a virtual terminal:
CTRL-ALT-F1
It tells me that X is still running and I need to exit it before running the "sh" command.
```
sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```


So I try either CTRL-ALT-BACKSPACE or I run
```
sudo /etc/init.dgdm stop
```
and the screen goes to a black screen with some scripts that seem to be running, but a login never comes up.  I have waited up to 10 min for the login to come up on this screen and it never does.

This process worked on this SAME machine in Ubuntu 6.10, but for some reason it doesn't want to work in Fiesty

---

### Post by RomeReactor on 2007-07-21
Hi. You can find the **1.0-9755** driver through Synaptic; search for **nvidia-glx-new**; or, from the terminal:
```
sudo apt-get install nvidia-glx-new
```

---

### Post by kc5hwb on 2007-07-21
Thanks, I have seen that before, but how do I confirm that is the latest driver?  The reason I ask is..

When I was running 6.10 I was told to run that from Synaptic and after doing so, I was still getting a choppy display and low-res screen resolutions.  Then I ran the downloaded file from NVIDIAs site and it worked perfectly.  So I just want to make sure that I am running the right driver.

This is the mobo I am running with the onboard GeForce 6100 graphics card..
[http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=332](http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=332)

---

### Post by kc5hwb on 2007-07-21
I went ahead and installed that from Synaptic and it does seem to work better, however I am getting a notification icon in the top-right of the screen next to the shutdown button that says...
[B]
Restricted Drivers In Use:
In order for this computer to function properly, Ubuntu may be using driver software that cannot be supported.  Because the software is proprietary, it cannot easily be changed to fix any future problems.[/B]

Will this pose any problems?

---

### Post by luctor on 2007-07-21
No :-)

---

### Post by regomodo on 2007-07-21
> **kc5hwb said:**
> 
```
sudo /etc/init.dgdm stop
```
and the screen goes to a black screen with some scripts that seem to be running, but a login never comes up.  I have waited up to 10 min for the login to come up on this screen and it never does.

This process worked on this SAME machine in Ubuntu 6.10, but for some reason it doesn't want to work in Fiesty

Are you sure you didn't type sudo /etc/init.d/gdm stop   ?

---

### Post by kc5hwb on 2007-07-21
thats a typo... yes I typed

```
sudo /etc/init.d/gdm stop
```

---

### Post by RomeReactor on 2007-07-21
> **kc5hwb said:**
> Thanks, I have seen that before, but how do I confirm that is the latest driver?  The reason I ask is.

When you search for nvidia-glx-new in Synaptic, look at the "Latest Version" column; it should read 1.0.9755+(KERNEL_HERE), the same as the latest version offered in the [Nvidia site]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html").

---

