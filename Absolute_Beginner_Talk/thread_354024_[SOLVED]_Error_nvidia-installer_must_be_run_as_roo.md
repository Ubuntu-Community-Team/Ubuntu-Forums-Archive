---
title: "[SOLVED] Error: nvidia-installer must be run as root"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-05
Hi

I've tried to update my nvidia driver(s) and received the above message. A previous post suggested that ubuntu doesn't use root privileges (I may not have expressed that right). Can anyone help?

NVIDIA-Linux-x86-1.0-9746-pkg1.run was what I was trying to execute.

---

### Post by compiledkernel on 2007-02-05
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run 

=)

---

### Post by Patrick K on 2007-02-05
Anything system related requires root privileges. In the terminal type sudo before the command.

---

### Post by ubername on 2007-02-05
> **compiledkernel said:**
> sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run 

=)


Thanks. 

The file showed on my desktop, so I copied it to my home directory (is that the right word?) and ran the command you gave.

ERROR: Unable to find the system utility `ld`; please make sure you have the
         package 'binutils' installed.  If you do have binutils installed,
         then please check that `ld` is in your PATH.

Was what happened. I clearly don't know my way around the linux file system.

Thanks for the help, It is a step forward.

---

### Post by Perfect Storm on 2007-02-05
Save the file to your Desktop

```

cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo /etc/init.d/gdm start

```

Good idea to print this as it will close X down.

---

### Post by ubername on 2007-02-05
> **Artificial Intelligence said:**
> Save the file to your Desktop

```

cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo /etc/init.d/gdm start

```

Good idea to print this as it will close X down.


Thanks for this. 


Can I just clarify what `uname -r` requires? my username is john

Do I type 'sudo apt-get install linux-headers- john -r build-essential gcc gcc-3.4 xserver-xorg-dev'

?

I will try in a minute but right now I don't have a printer to hand. It scares me that I might have to type in commands, it is so many years since I have used  a command line!

---

### Post by Perfect Storm on 2007-02-05
No it have to be exactly as I posted above. It's a command that find which type of kernel you have installed and out from that it download the right headers.


If it fails you type
```
sudo nano /etc/X11/xorg.conf
```

and change "nvidia" back to "nv" in Driver under Section "Device" and you'll be rolling again.

---

### Post by newbsaucer on 2007-02-05
> **Artificial Intelligence said:**
> If it fails you type
```
sudo nano /etc/X11/xorg.conf
```

and change "nvidia" back to "nv" in Driver under Section "Device" and you'll be rolling again.

You know I think this may have answered my question as to how i fubared my machine. Thanks!

---

### Post by steve.horsley on 2007-02-05
> **Artificial Intelligence said:**
> Save the file to your Desktop

```

cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo /etc/init.d/gdm start

```

Good idea to print this as it will close X down.

Very good, but I suspect it won't work if you copy and paste those commands into a GUI terminal window (which would be most people's reaction) because the gdm stop will terminate things there. This needs to be done in a text console.

---

### Post by Perfect Storm on 2007-02-05
That's why I warned him about it will close X and he properly want to write/print the suggestion.

---

### Post by ubername on 2007-02-05
> **Artificial Intelligence said:**
> Save the file to your Desktop

```

cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo /etc/init.d/gdm start

```

Good idea to print this as it will close X down.

Printed.

First step worked.

Second step:

john@john-desktop:~/Desktop$ sudo apt-get install linux-headers- 'uname -r' build-essential gcc gcc-3.4
Reading package lists... Done
Building dependency tree... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package uname -r



Any clues?

Thanks in advance.

EDIT : Well, I would have helped if I had actually followed the instructions!

---

### Post by old_geekster on 2007-02-05
Follow this guide and you will have no problems:

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=Hub](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=Hub)

I have used it several times, without any problems.

Be sure to make notes where he recommends it.  You will need them.

---

### Post by ubername on 2007-02-05
It worked I think, (although I got lots of messages about packages not being installed) as far as 

sudo sh NVIDIA-linux.........

When it said something along the lines of 'sh not found'

I couldn't cut and paste the message presumably because my GUI had gone, I also struggled to restart the beast until I tried 'sudo shutdown -r now'.

You learn quickly here!

---

### Post by bodhi.zazen on 2007-02-05
Envy is an easier way to install and maintain the nvidia drivers ...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ubername on 2007-02-05
> **bodhi.zazen said:**
> Envy is an easier way to install and maintain the nvidia drivers ...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Looks good. I have clicked the link, downloaded it to desktop, installed it. Now what do I do?

EDIT: Must stop posting before I have read instructions properly!

---

### Post by ubername on 2007-02-05
> **ubername said:**
> Looks good. I have clicked the link, downloaded it to desktop, installed it. Now what do I do?

EDIT: Must stop posting before I have read instructions properly!

Job done, screen much easier to read, thanks to all. I have learned a lot from your help even if I ended up using a package..

---

### Post by das letzte einhorn on 2008-03-21
I have the same issue than him. I did exactly as told, but once the X server shuts down my commands are not recognized. I typed sudo sh ... , but once I press enter it basically skips to the next line. Is there another key which should be pressed instead?

---

