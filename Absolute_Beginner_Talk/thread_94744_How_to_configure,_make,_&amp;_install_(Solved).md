---
title: "How to configure, make, &amp; install (Solved)"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by Centrist on 2005-11-24
I have the source to a program that I want to install. The readme tells me that I need to use the 'make' and 'install' commands to use it. So what do I have to do to install the make program? And what arguments do I need for the install command?

---

### Post by Leif on 2005-11-24
sudo apt-get install build-essential
cd to the src dir
./configure
make
sudo make install

---

### Post by aysiu on 2005-11-24
Are you sure you want to install it from source? There are other ways, too. Please see both links in my sig.

---

### Post by oskude on 2005-11-24
[QUOTE=Centrist]I have the source to a program that I want to install.[/QUOTE]do you really (i mean REALLY) want to build it by yourself, see the previous post...
[QUOTE=Centrist]The readme tells me that I need to use the 'make' and 'install' commands to use it.[/QUOTE]i assume it also says where to use these commands...
[QUOTE=Centrist]So what do I have to do to install the make program?[/QUOTE]
"apt-get install make", but your better off with "apt-get install build-essential"
[QUOTE=Centrist]And what arguments do I need for the install command?[/QUOTE]you mostly dont "need" any, but "./configure --help" is a start

and for "sudo make install" i would recommend "sudo checkinstall", this gives you a nice deb file and you can remove the program with "dpkg -r programname"

---

### Post by Ruso on 2005-11-24
2 aysiu

Can you explain why its better to install the software from packages rather then from source??

---

### Post by Leif on 2005-11-24
[QUOTE=Ruso]2 aysiu

Can you explain why its better to install the software from packages rather then from source??[/QUOTE]

will field this one, hope aysiu doesn't mind :) 

installing from the repositories means that everything will be nicely integrated, and will update automatically. if you're not using apt in a debian-derived distro, you're missing half the point.

---

### Post by tokyovigilante on 2005-11-24
Have you searched Synaptic for the program you want to install? What is it precisely?

In addition to the above advantages of using packages, you don't have to wait for it to compile (which is good if you have a large program on a slow computer) you can easily uninstall/reinstall it, any extra software needed to run the program ("dependencies") will be automatically installed at the same time, and if it is in the main or universe repositories, then it will have recieved at least a little testing to ensure it is compatible with Ubuntu.

---

### Post by oskude on 2005-11-24
[QUOTE=Ruso]Can you explain why its better to install the software from packages rather then from source??[/QUOTE]can you explain why its better to get a "ready-build" car, rather than to build a car by yourself ;)

knowledge ! 

its way more easy to just click a button and the program will be automaticly installed and configured... 
(thats why people buy things, and not DIY. and use apt-get instead of compiling)

so, you should know your way in gnu/linux before you compile :!:

but no, (with knowledge) building a program by yourself is not "hard" at all (my best case was just typing "scons (install)", ready)

---

### Post by Centrist on 2005-11-24
Thanks, Leif, that worked fine. ;)

The program is a proprietary DNS update client so it wouldn't be in a repository.

---

