---
title: "Nvidia driver install help please"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by maxim1 on 2007-04-06
I am trying to install the Nvidia drivers and need help. I have been to the Nivida web siite and serached the forums. What I have found which relates to my problems is below. I am new to linux and find it hard to understand the terminology used can any one explain.

Installing the Kernel Interface
The NVIDIA kernel module has a kernel interface layer that must be compiled specifically for each kernel. NVIDIA distributes the source code to this kernel interface layer, as well as precompiled versions for many of the kernels provided by popular Linux distributions.

When the installer is run, it will determine if it has a precompiled kernel interface for the kernel you are running. If it does not have one, it will check if there is one on the NVIDIA FTP site (assuming you have an Internet connection), and download it. If one cannot be downloaded, either because the FTP site cannot be reached or because one is not provided, the installer will check your system for the required kernel sources and compile the interface for you. You must have the source code for your kernel installed for compilation to work. On most systems, this means that you will need to locate and install the correct kernel-source, kernel-headers, or kernel-devel package; on some newer distributions, no additional packages are required (e.g. Fedora Core 3, Red Hat Enterprise Linux 4).

Note that linking of the kernel interface (in the case that the interface was downloaded or compiled at installation) requires you to have a linker installed on your system. The linker, usually /usr/bin/ld, is part of the binutils package. If a precompiled kernel interface is not found, you must install a linker prior to installing the NVIDIA driver.

---

### Post by Maestro23 on 2007-04-06
Installing Nvidia Drivers: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
or
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

*Envy script does the legwork for you.  Many use it and have success.

---

### Post by Spike-X on 2007-04-06
Yeah, doing it with Envy is a piece of cake.

---

### Post by maxim1 on 2007-04-06
cheers thanks a lot

---

