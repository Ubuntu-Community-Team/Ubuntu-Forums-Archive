---
title: "Graphics issue with Ubuntu Server"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Stormweaver on 2007-04-22
First off, how can I tell if I have "make"  and  "gcc"


Second, can Ubuntu 386 Server have 3D or no?? I know you can't have GLX from Nvidia, so what happens, is that the end of 3D enviroment or does Open GL just have to be set up differently?

---

### Post by Bachstelze on 2007-04-22
3D on a server ??

---

### Post by Stormweaver on 2007-04-22
Yes, I have 386 server set up so that I can handle server functions but I also applied GUI to it so that I can use this system for other things, such as a second log in point for WoW when I need to access a second account for a bit.

Getting the WoW installed is not the priority here yet as I can't seem to get Open GL rolling on this system.

---

### Post by Bachstelze on 2007-04-22
Oh, so you're basically running a desktop with Apache and friends installed on it ? I suggest you switch to the generic kernel and install your nvidia drivers normally.

---

### Post by Stormweaver on 2007-04-22
What about server functions such as Team Speak and Web Hosting et all?

Or you saying switch to Desktop and install the extra server functions?

---

### Post by Bachstelze on 2007-04-22
Obviously, installing a server and then the desktop functions or installing a desktop and then the server fuctions will give the same results in the end. The problem is that you're running a kernel specifically designed for "pure" servers, so that could very well be why you're experiencing problems with your nvidia drivers. What I'm telling you to do is intall the "generic" kernel, which is the default one used on desktop systems. This will of course not affect the "server functions", as they're not kernel-dependent.

```
sudo apt-get install linux-generic
```

---

### Post by Stormweaver on 2007-04-22
Do I dump what I have here already???

Or will that sudo you posted deal with all the above?

---

### Post by Stormweaver on 2007-04-22
I mean --- I've not got all the extra software for the server except Teamspeak set up... So if I need to change OS, I can do it now, but I need to know what to change to that I can handle my Server funtions as well as my Graphical wants and needs.

---

### Post by Bachstelze on 2007-04-22
No, you just need to change your kernel, that command I gave you above should do the trick (and a reboot, obviously).

---

### Post by Stormweaver on 2007-04-22
Ok -- I'm off to do that command, could I get some aid on return to straighten things out?

Thanks!

---

### Post by Stormweaver on 2007-04-22
Ok - Installed that sudo command - The gdm crashed during start up saying that 

Failed to start the X Server (your grahpical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem


I went into Xorg.conf and changed the driver to vesa -- Just to get back to where I could post this... My graphics are back to choppy -- I assume something needs to be installed or mod'ed, but I don't know what to do from here... 

Help Please!

---

### Post by Bachstelze on 2007-04-22
Since you installed a new kernel, you obviously need to reinstall your nvidia drivers.

---

### Post by Stormweaver on 2007-04-22
Ok do I install them via - Nvidia.com, Automatix, or Synaptic?

---

### Post by Bachstelze on 2007-04-22
Nvidia or Synaptic, as you wish. Please don't use Automatix.

---

### Post by Stormweaver on 2007-04-22
Ok - I went with Nvidia, nothing better then the source right??

It gave me an error about sources and stuff, and I remembered when doing that kernal sudo you gave, that it had some recommended packages, so I went to install them, got the the nvidia-glx-legacy one and it came back with this

The following packages have unmet dependencies:
  nvidia-glx-legacy: Conflicts: nvidia-glx
E: Broken packages
stormweaver@Eye-of-the-Storm:~$ 

I dunno what to do next?

---

### Post by Stormweaver on 2007-04-22
Never mind.. I'm stupid.....


Hang on while I try to install these

---

### Post by Bachstelze on 2007-04-22
Nope, if you want to use the installer from nvidia, you need to remove and install a bunch of stuff :

```
sudo apt-get remove linux-restricted-modules* nvidia-glx
sudo apt-get install build-essential linux-headers-$(uname -r) xorg-dev pkg-config
```

---

### Post by Stormweaver on 2007-04-22
Which do I want? nvidia-glx or nvidia-glx-legacy ??? I tried for the second and it wanted to un install the first.

---

### Post by Stormweaver on 2007-04-22
I just caught your post....

So I am gonna end up right where I was......

I had the other driver installed  without GLX and with those other mods in place.. everytime I tried to run a 3D enviroment it crashed saying there was no Open GL...


What do I do?

---

### Post by Bachstelze on 2007-04-22
The nvidia-glx is needed if you want to use the driver from the Ubuntu repos. If you want to use the installer from nvidia, you must remove the Ubuntu package first to avoid conflicts.

---

### Post by Stormweaver on 2007-04-22
Ok - I am seeing through the cloud a bit again...

I followed those two commands

Now I assume I got Cntl Alt F1 -- Stop gdm and do the installer?

---

