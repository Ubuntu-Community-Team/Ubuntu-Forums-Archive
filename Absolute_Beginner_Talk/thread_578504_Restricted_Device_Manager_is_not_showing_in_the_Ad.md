---
title: "Restricted Device Manager is not showing in the Administration menu"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by WerX on 2007-10-17
I am running feisty with all the latest updates. I've done this before and never had this problem, but the Restricted Device Manager is not in the System > Administration menu which I found confusing :) 

I have an Nvidia 5200fx card.

 lspci | grep -i nvidia returns

0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Any ideas why I'm not seeing the restricted device manager? and how I would go about installing the proprietary nvidia drivers?

Cheers

---

### Post by Baby Boy on 2007-10-17
Try to find the *restricted-manager* in the *usr/bin*.

---

### Post by aktiwers on 2007-10-17
I have no idea why its no showing.. but you can install them manually by doing this.



Go here and download the latest driver:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1

Log in.
type:
```
sudo /etc/init.d/gdm stop
``````
cd Desktop
```And then 
```
sudo ./NVIDIA-Linux-x86-100.14.19-pkg1.run
```when done.. type:
```
sudo reboot
```

---

### Post by WerX on 2007-10-17
> **Baby Boy said:**
> Try to find the *restricted-manager* in the *usr/bin*.

It isn't there heh. I will try the instructions the other guy gave for installing them.

---

