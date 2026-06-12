---
title: "Best Method To Install Files."
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by zaden.winkler on 2007-09-27
I am rather new and i would love to know the best method to install files.

1.Source files
2. .deb
3. .rpm
4. and other types


Please note this machine will not be connected to the internet at all. So wget or apt will not work for me.

please also tell me if there are any tools i need to download to ensure my ability to install anything i would like to

---

### Post by justleen on 2007-09-27
the best way to install files, is trough packages. both .rpm and .deb are packages.. BUT! rpm is for red hat based distribution, .deb for debian based ones. 
Ubuntu is a debian based distribution. Most application come in both flavours, so you'll have to slecet the .deb files.

Better still (better, as in no typing required..) is to use the package manager
you'll find it under System > Adminstration > Synaptic package manager.

---

### Post by PmDematagoda on 2007-09-27
My best installer in my opinion is "apt-get", after that .deb's, then Synaptic, Add & Remove, and lastly Automatix.

---

### Post by notwen on 2007-09-27
I'd go with a GUI like Synaptic and/or Add/Remove, then apt-get from CLI, then .deb files, and lastly the compiling from source.  Dependencies always could play an issue with your ability to install something and have it run w/o issue, the first two nearly always take care of those and .deb files generally do as well, while compiling is.. well compiling.  =p  I wouldn't recommend compiling form source to a beginner, but sometimes you'll find yourself stuck having to use CLI and generally there is a walk-through w/ step-by-step instructions. =]

---

### Post by hyper_ch on 2007-09-27
First is apt-get (can also be from a cd or dvd containing the packages) and then the dpkg with the .deb files...

Synaptic is just a graphical front-end for apt-get... Add& Remove is the same...

Automatix is not a good way to install anything...

---

