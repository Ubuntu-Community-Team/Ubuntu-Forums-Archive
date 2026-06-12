---
title: "edit xconfig file"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Slyth99 on 2005-10-08
What is the best program to use while editing xconfig file to change nvidia drivers settings?

---

### Post by heimo on 2005-10-08
Your favourite text editor. That could be kwrite, gedit, nano... (I would recommend nano as it's easy to use and works in pure text mode too - without graphical user interface). Are you using Warty or Hoary? In Hoary X configuration is in file /etc/X11/xorg.conf If you have any specific questions about editing this file, don't hesitate to ask.

I can see you're relatively new to Ubuntuforums, so - welcome! :)

EDIT: If you only want to change from nv to nvidia, you should probably just run
```
 sudo nvidia-glx-config enable
```

---

### Post by Slyth99 on 2005-10-08
How do i access one of those editors with x turned off? I am trying to upload the latest nvidia driver with little success.

---

### Post by heimo on 2005-10-08
On virtual terminal / without X, on the command line you typically start editor with command like this:
```
nano /etc/X11/xorg.conf
``` where nano is the editor you want to use and the rest of the line is the file you want to edit.

Which instructions are you following to install nvidia drivers? I'll try to find you a howto. (There are several on these forums, I think.)

The easy way:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
[http://www.ubuntuguide.org/#installnvidiadriver]("http://www.ubuntuguide.org/#installnvidiadriver")

Harder way (latest drivers):
[http://ubuntuforums.org/showthread.php?t=57368]("http://ubuntuforums.org/showthread.php?t=57368")

---

### Post by Slyth99 on 2005-10-08
I have a problem as i don't have the source kernel on my system and i get a message saying i need it. I am just downloading the latest kernel now. Are there any other things i need to download. I don't have the internet on the computer with Ubuntu on it so I have to use Uni computers with broadband to download stuff. If there is anything else I need it would be a great help to let me know. :)

---

### Post by heimo on 2005-10-08
I think it would be easiest for you to use these instructions:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")

You don't get the latest drivers, but it will be a bit easier to install. 

I'm not sure about all the dependent packages that are not yet installed, but at least you need "nvidia-kernel", one of these:
[http://packages.ubuntu.com/hoary/virtual/nvidia-kernel-1.0.7167]("http://packages.ubuntu.com/hoary/virtual/nvidia-kernel-1.0.7167")

And more specifically, for example for Pentium 4 processors:
[http://packages.ubuntu.com/hoary/base/linux-image-2.6.10-5-686]("http://packages.ubuntu.com/hoary/base/linux-image-2.6.10-5-686")
[http://packages.ubuntu.com/hoary/misc/linux-restricted-modules-2.6.10-5-686]("http://packages.ubuntu.com/hoary/misc/linux-restricted-modules-2.6.10-5-686")
[http://packages.ubuntu.com/hoary/x11/nvidia-glx]("http://packages.ubuntu.com/hoary/x11/nvidia-glx")

You may already have the kernel installed, important part is the restricted modules and nvidia-glx (also: modules package must match the kernel version you will be using). If you want to install latest nvidia drivers, I believe you need at least some of the packages from build-essential package and linux-headers package for you current kernel. I might be wrong.


EDIT: This is _so_ much easier when you have network connection. :) If you can get your computer to network termporarily, that'd be the way I'd do it.

---

