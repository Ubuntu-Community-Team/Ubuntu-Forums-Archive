---
title: "[SOLVED] Installing Programs"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by chriss8892 on 2007-11-15
So, I'm pretty new to ubuntu, and I've tried to install programs such as limewire,songbird, and my nvidia geforce 6600 video card driver, but none of them seem to install properly, i get error messages and "file cannot be found" quotes, if anyone could help me with this i'd greatly appreciate it.

---

### Post by Inxsible on 2007-11-15
You can install software in ubuntu in 4 different ways
1)```
sudo aptitude install *package-name*
``` or ```
sudo apt-get install *package-name*
```

2) Applications>>Add/Remove . Search and install the application.

3) System>>Administration>>Synaptic Package Manager. Search and install application/package.

4) Compile from source.

---

### Post by chriss8892 on 2007-11-15
i tried all of those, there must be something i'm doing wrong because none of these programs show up in the add/remove app list

---

### Post by Inxsible on 2007-11-15
> **chriss8892 said:**
> i tried all of those, there must be something i'm doing wrong because none of these programs show up in the add/remove app listNot all programs have a menu entry. what specific program are you trying to install?

---

### Post by chriss8892 on 2007-11-15
limewire, songbird, and my nvidia driver

---

### Post by Inxsible on 2007-11-15
i dont think any of them are in synaptic. so you probably had to download the .deb file or compile from source. which one did you do ?

---

### Post by chriss8892 on 2007-11-15
i downloaded all of them, particularly im working on trying to get songbird to work

---

### Post by Inxsible on 2007-11-15
> **chriss8892 said:**
> i downloaded all of them, particularly im working on trying to get songbird to work
you are still not answering the question. was it a deb file that you downloaded ?

---

### Post by Inxsible on 2007-11-15
or where did you download the file from?

---

### Post by chriss8892 on 2007-11-15
sorry didn't know what you were talking about at first, and yea it was

---

### Post by jfinkels on 2007-11-15
Install frostwire instead of limewire by typing the following in the terminal:```
sudo aptitude install frostwire
```

You're going to have to download the source for songbird and compile it from source, which may be difficult if you're new to Linux. See the link in my signature about "Installing software". Read it thoroughly.

There are generally two drivers for nVidia cards on Linux, the open source "nv" driver and the proprietary "nvidia" driver. To see which one you are using, open the file /etc/X11/xorg.conf and find the section that starts with "Section 'Device'", and look next to the entry for "Driver" beneath that.

EDIT: see the UbuntuGuide for more info on installing the nVidia driver [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver)

---

### Post by chriss8892 on 2007-11-15
> **Inxsible said:**
> or where did you download the file from?

the host websites, limewire.com/nvidia.com etc.

---

### Post by Inxsible on 2007-11-15
you can install the nvidia driver by going to System>>Administration>>Restricted Driver Manager. and simply enabling the driver.

---

### Post by chriss8892 on 2007-11-15
> **Inxsible said:**
> you can install the nvidia driver by going to System>>Administration>>Restricted Driver Manager. and simply enabling the driver.
yes i tried that but it said

[B][I]The software source for the package

   nvidia-glx-new

 is not enabled.[/I][/B]

---

### Post by Inxsible on 2007-11-15
> **chriss8892 said:**
> yes i tried that but it said

[B][I]The software source for the package

   nvidia-glx-new

 is not enabled.[/I][/B]Have you enabled the universe and multiverse repos?

you can do this by System>>Administration>>Software Sources. Check mark the universe and multiverse repos. then try the restricted driver thing again.

---

### Post by chriss8892 on 2007-11-15
> **Inxsible said:**
> Have you enabled the universe and multiverse repos?

you can do this by System>>Administration>>Software Sources. Check mark the universe and multiverse repos. then try the restricted driver thing again.

I checkmarked all of them and it worked, thank you soooo much

---

### Post by Inxsible on 2007-11-15
> **chriss8892 said:**
> I checkmarked all of them and it worked, thank you soooo much
no problem. glad to help.

mark your thread as solved by Thread Tools>>Mark thread as solved. :)

---

