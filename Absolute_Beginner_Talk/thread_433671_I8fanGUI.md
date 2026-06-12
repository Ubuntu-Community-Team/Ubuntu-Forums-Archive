---
title: "I8fanGUI"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by philby on 2007-05-05
Hi - I'm slowly coming to grips with Ubuntu, but I have one issue that has really stumped me. I have installed a program called I8Kutils which allows me to control the cooling of the graphics card and CPU but I can't find the program. Under the Synaptic manager it seems installed but I can't find it under add/remove and don't know how to get this program operational, or in fact were to actually find it. i've tried a search but don't know where it exists.

On a positive note Beryl was easy to get going and the 3D effect seems great.

---

### Post by starcraft.man on 2007-05-05
I'm pretty sure that the given program if its installed should be launchable via the terminal, just open the terminal and type the name in and push enter. If it needs root access preface it with sudo. If it returns an error, its likely not installed properly or at all.

---

### Post by Alterios on 2007-05-05
if you are not sure about the command to run it from the command line you can do the following: 
open synaptic, search for I8Kutils, one it shows up right click on it and select properties, under the installed files tab you need to look for the commands in the bin directories i.e. /usr/bin/I8Kutils or /bin/I8Kutils
The command after the bin/ is the command you type into the command line to start it. This can be done with any file installed by apt-get.

---

### Post by toorima on 2007-05-05
I recommend installing gkrellm and the gkrellm-i8k plugin, lets you set at what temps the fans should go on and off and also gives you info about temps etc

if you get an error with i8k you must do the following
sudo modprobe i8k force=1
sudo gedit /etc/modules
add the following line to the end of the file: i8k force=1

---

### Post by philby on 2007-05-05
> **toorima said:**
> I recommend installing gkrellm and the gkrellm-i8k plugin, lets you set at what temps the fans should go on and off and also gives you info about temps etc

if you get an error with i8k you must do the following
sudo modprobe i8k force=1
sudo gedit /etc/modules
add the following line to the end of the file: i8k force=1

Thanks Toorima - this was 100% correct Utility is working within the gkrellm but also had the error which was fixed by the script. Not to sure if this utility is as good as the O'l iK8fangui but it did kick in my fans - don't like my poor old GPU idling at 70degC !!!!

Thanks again:guitar:

---

