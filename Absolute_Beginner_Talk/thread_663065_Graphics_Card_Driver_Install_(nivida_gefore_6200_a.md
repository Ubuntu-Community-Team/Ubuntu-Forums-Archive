---
title: "Graphics Card Driver Install (nivida gefore 6200 agp)"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by computernub1 on 2008-01-09
Hi, I am a new Ubuntu user but have noticed that my computer is a little, but noticably slower then when it was on Windows. I am assuming i need to install a driver for my graphics card.
I have a Nvidia GeForce 6200 AGP 256 MB.

How would I do this? Thank you very much in advance.

---

### Post by taurus on 2008-01-09
Go into System -> Administration -> Restricted Drivers Manager and install nvidia driver for your graphic card.  You need to reboot (or at least restart X) after you install it.

---

### Post by RomeReactor on 2008-01-09
Hi. Go to 'System->Administration->Restricted Drivers Manager' and check the box for your card; that will install the proprietary nVidia drivers, which should give you smoother performance.

---

### Post by aktiwers on 2008-01-09
Do like this (To install the newest version Manually):
```
sudo aptitude install libc6 libc6-dev
``````
sudo aptitude install build-essential linux-headers-$(uname -r);
```Go here and download the latest  driver:
[http://www.nvidia.com/object/linux_d...32_169.07.html]("http://www.nvidia.com/object/linux_display_ia32_169.07.html")
(here is the main link [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html))

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1
Log in
 type:

```
cd Desktop
``````
sudo /etc/init.d/gdm stop
``````
sudo chmod +x NVIDIA-Linux-x86-169.07.pkg1.run
```And then
```
sudo ./NVIDIA-Linux-x86-169.07.pkg1.run
```After that reboot
```
sudo reboot
```

---

