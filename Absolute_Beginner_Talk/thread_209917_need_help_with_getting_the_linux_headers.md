---
title: "need help with getting the linux headers"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by mycoplasma on 2006-07-05
I am trying to install new nvidia drivers for my dapper drake machine.  I am using method 2 detailed at [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) .  However, when i enter 

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

into BASH to get the headers, it says

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-23-amd64-generic

could anyone please help me with this problem?

---

### Post by simonn on 2006-07-05
Try installing linux-headers-2.6.15-23-amd64-generic through synaptic.

---

### Post by Kilz on 2006-07-05
[QUOTE=mycoplasma]I am trying to install new nvidia drivers for my dapper drake machine.  I am using method 2 detailed at [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) .  However, when i enter 

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

into BASH to get the headers, it says

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-23-amd64-generic

could anyone please help me with this problem?[/QUOTE]
You may need to enable the universe or multiverse to get them. You can do that in synaptic, click settings, repositories, then add, then check the boxes.

---

### Post by catlett on 2006-07-05
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html) Why don't you try "envy". It is a script that automates the installation of nvidia drivers. It was written by Alberto Milone who posts by the name of "Tselliot". He is an Ubuntu Forum Staff Member. I used it and it worked flawlessly for me.
Just thought I would throw out a suggestion.

P.S. The Dapper guide only has one command for the driver. I did not install this way but again I thought I'd mention it.
```
sudo apt-get install nvidia-glx nvidia-kernel-common
``` From here [http://doc.gwos.org/index.php/DapperGuide#How_to_install_Graphics_Driver_.28NVIDIA.29](http://doc.gwos.org/index.php/DapperGuide#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

