---
title: "[SOLVED] How do I kill X?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by spydon on 2007-12-25
Hi.
Does anyone know how to kill X and not just restart it like ctrl+alt+backspace.
I need to do this to install a nvidia driver.

---

### Post by overdrank on 2007-12-25
> **spydon said:**
> Hi.
Does anyone know how to kill X and not just restart it like ctrl+alt+backspace.
I need to do this to install a nvidia driver.

[http://ubuntuforums.org/showthread.php?t=649215](http://ubuntuforums.org/showthread.php?t=649215)

---

### Post by The Cog on 2007-12-25
**sudo /etc/init.d/gdm stop**
and later:
**sudo /etc/init.d/gdm start**

But unless you have good reason not to, I recommend that you install the nvidia driver from the repositories rather than from the nvidia website - it will make life much easier when you next install a kernel security update. Security updates to the kernel always are always accompanied by an update to the driver in the repository if needed, but the one straight from the nvidia site will need recompiling (without a GUI) before it works again.

---

### Post by bumanie on 2007-12-25
But unless you have good reason not to, I recommend that you install the nvidia driver from the repositories rather than from the nvidia website - it will make life much easier when you next install a kernel security update. Security updates to the kernel always are always accompanied by an update to the driver in the repository if needed, but the one straight from the nvidia site will need recompiling (without a GUI) before it works again.

Iagree with the sentiments of your comments, but I had to install a nvidia llegacy linux driver by stopping x as you described. For my graphics card (fairly old) I could find any other way to install it. When I tried 'a how to install nvidia card into gutsy', I was left with a monitor turning itself off and on every two seconds. Unless you know of a specific way to install older cards (which I would like to know how to do), I think for some older cards may be the only way.

---

### Post by The Cog on 2007-12-25
Ther eis a package called nvidia-glx and a nvidia-glx-new in the repos. If neither of those support your card, that is a good reason for going to the nvidia site. I would be surprised if the driver from the nvidia site had more support for old cards, but its worth a try. You will need to install package** build-essential ** in order to be able to compile the driver.

---

### Post by bumanie on 2007-12-25
For my card I needed nvidia glx legacy. I don't think the legacy is catered for in the repositories. I could be wrong though. I'm presently on a windows machine and can't check.

---

### Post by The Cog on 2007-12-25
nvidia-glx-legacy is there in the repositories. If thi sis the one you need, youshould definitely use the repository version rather than download from nvidia.

---

### Post by aktiwers on 2007-12-25
This is how you install them manually:

Go here and download the latest  driver:
[http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html)
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
```when done.. type:
```
sudo reboot
```

---

### Post by spydon on 2007-12-25
> **aktiwers said:**
> This is how you install them manually:

Go here and download the latest  driver:
[http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html)
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
```when done.. type:
```
sudo reboot
```

Yes I know, I just wanted to know how to stop x. :P

xorg was f*cked up after I used the driver from their website so I don't recommend it. It is an geforce 8500 gt and it works pretty good with the restricted driver but it doesn't work perfectly, when I for example set it to 85hz it gets 50hz and ubuntu says it's using 85hz but my screen and my eyes says that it is 50hz :P. Well I will mark this thread as solved because all I wanted to know was how to stop X. Thx all.

---

