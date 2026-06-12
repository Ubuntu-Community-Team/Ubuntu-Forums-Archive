---
title: "2 hours in, already frustrated"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by sirgawain on 2006-06-26
Okay, I wanted to give this product a try.  My system is a Dual core 3GHZ machine with scads of ram and drive space.  I have an NVIDIA GEFORCE 6800 hooked up to the 24" widescreen Dell monitor.  So far, here are my impressions:

- I can never pull up the device manager without it locking up.  Well, not entirely true, I can do it one time then never again without rebooting.

- I installed the nvidia drivers, but have no idea where to go to set things up.  my resolution is right now fixed at 1024x768 on a monitor that can push a lot more.  

I am guessing that you have to go deep into the system to make this stuff work?  it's not working right out of the box?

Any help would be appreciated.  I don't know if SuSe or Fedora would do a better job out of the gate, but I've heard a lot of good things about Ubuntu and wanted to give it a fair shake before trying the others.

Thanks for any help!

---

### Post by bruce89 on 2006-06-26
[QUOTE=sirgawain]- I can never pull up the device manager without it locking up.  Well, not entirely true, I can do it one time then never again without rebooting.[/QUOTE]
Try this - ```
hal-device-manager
``` and note any output here.
[QUOTE=sirgawain]- I installed the nvidia drivers, but have no idea where to go to set things up.  my resolution is right now fixed at 1024x768 on a monitor that can push a lot more.  
[/QUOTE]
```
sudo dpkg-reconfigure xserver-xorg
```, select the nvidia driver.  Resolution detection seems to be a major issue, it got mine wrong too.

---

### Post by kaamos on 2006-06-26
Hello and welcome to the forums!

> 
- I installed the nvidia drivers, but have no idea where to go to set things up. my resolution is right now fixed at 1024x768 on a monitor that can push a lot more.

Go to Applications->Accessories->Terminal and copy & paste this there
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
you should get a prompt where you can set you resolution. After that press ctrl+alt+backspace to restart the graphic system. If you need more options than the resolution, use the same command but leave out the "-phigh".

You can find more info at [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
That wiki is also otherwise a great resource.

Hope this helps!

---

### Post by tseliot on 2006-06-26
[QUOTE=sirgawain]- I can never pull up the device manager without it locking up.  Well, not entirely true, I can do it one time then never again without rebooting.[/QUOTE]
You shouldn't have that problem. However I find the device manager quite useless (it's not like Windows' control panel).

[QUOTE=sirgawain]- I installed the nvidia drivers, but have no idea where to go to set things up.  my resolution is right now fixed at 1024x768 on a monitor that can push a lot more.[/QUOTE]
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

---

