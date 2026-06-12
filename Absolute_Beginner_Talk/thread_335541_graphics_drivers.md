---
title: "graphics drivers"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by rgp-02 on 2007-01-10
newbie to linux w/new install of ubuntu needs to know in simple english:

where do i get drivers for GeForce 7600 GS?

how do i install them?

---

### Post by kj1h234lkj1234 on 2007-01-10
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by rgp-02 on 2007-01-10
rp@rgp-02:~$ sudo apt-get install nvidia-glx nvidia-kernel-common
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-kernel-common is already the newest version.
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4066kB of archives.
After unpacking 12.6MB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted nvidia-glx 1.0.8776+2.6.17.7-10.1 [4066kB]
Fetched 4066kB in 3s (1129kB/s)      
Selecting previously deselected package nvidia-glx.
(Reading database ... 88784 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.17.7-10.1_i386.deb) ...
Setting up nvidia-glx (1.0.8776+2.6.17.7-10.1) ...

rp@rgp-02:~$ 




i'm left in suspense here......what's it mean?

---

### Post by petriomelony on 2007-01-10
> **rgp-02 said:**
> newbie to linux w/new install of ubuntu needs to know in simple english:

where do i get drivers for GeForce 7600 GS?

how do i install them?

which version of ubuntu are you using?

---

### Post by ajgreeny on 2007-01-10
It means you have successfully installed the nvidia driver you asked to be installed.

This is the standard output of apt-get install.  You will always see something similar if all goes well, and error messages saying something could not be installed and the reasons why, if there are problems.

---

### Post by rgp-02 on 2007-01-10
Thank you very much for replies and help!

---

