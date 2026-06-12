---
title: "NVIDIA driver.run file-How to install?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by WiRU on 2007-05-07
Ok, i downloaded this file:
NVIDIA-Linux-x86-1.0-9755-pkg1.run
I put in the desktop, typed "cd ~/Desktop" in the terminal, then "./NVIDIA-Linux-x86-1.0-9755-pkg1.run" and after the installer had started up it said that it must be run as a root.
Moreover, I tried typing "sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run"  instead. So I entered my password but after that the installer popped up saying "You appear to be running an X server; please exit X before installing."
Now what the heck do those messages mean? How can open the file? Is this the wrong forum to post this, does it belong to the nvidia forum?
Thanks

---

### Post by Sef on 2007-05-07
Are you running Feisty?  If so, then System > Administration > Restricted Drivers Manager.  That should automatically install the drivers you need.

---

### Post by justleen on 2007-05-07
you cannopt have a X server (eg, your gnome windows) running when installing this.
you can switch to a terminal, by pressing CTRL-ALT-F2.
logon here
stop X (=Gnome) by typing ```
sudo /etc/init.d/gdm stop 
```
then run the nvidia file.
start X again by typing ```
sudo /etc/init.d/gdm start 
```

Keep in mind, you do need the kernel headers to install the drivers!

(you might be better of by simply installing them from the repositries..)
```
sudo apt-get install nvidia-glx 
```

---

### Post by WiRU on 2007-05-07
NVIDIA accelerated graphics driver is enabled and in use, but is it the latest one? Does the manager automatically download the latest drivers?

---

### Post by WiRU on 2007-05-07
> **justleen said:**
> you cannopt have a X server (eg, your gnome windows) running when installing this.
you can switch to a terminal, by pressing CTRL-ALT-F2.
logon here
stop X (=Gnome) by typing ```
sudo /etc/init.d/gdm stop 
```
then run the nvidia file.
start X again by typing ```
sudo /etc/init.d/gdm start 
```

Keep in mind, you do need the kernel headers to install the drivers!

(you might be better of by simply installing them from the repositries..)
```
sudo apt-get install nvidia-glx 
```


I will try that

---

### Post by justleen on 2007-05-07
you shouldnt have to, if its already enabled!

```
glxinfo|grep version
```
that will output some glx info.. if it says nvida, your good..

---

### Post by moredhel on 2007-05-07
you could use envy, which is a script that will get you the latest drivers for nvidia or ati cards:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It also uses the one off the nvidia website and so will always be the latest drivers ;)

---

### Post by WiRU on 2007-05-07
okay thanks. 

I reinstalled feisty fawn. The drivers messed it up. The x server got destroyed.

---

### Post by steve.horsley on 2007-05-07
I'm sure it could have been fixed, but reinstalling may well have been the quicker option. I installed my drivers by going into synaptic and installing the package nvidia-glx-new. However, I since discovered that there is this Restricted Drivers Manager that Sef mentioned, which is probably even easier. I suggest you try that.

nvidia-glx-new is driver version 9755,  which is the same version as is on the nVidia web site downloads page.

---

### Post by WiRU on 2007-05-07
I went to enable the driver using the manager, and while it was downloading nvidia-glx-new, i noticed that is was downloading another version, so i cancelled it and found out it was downloading this:
nvidia-glx_1.0.9631+2.6.20.5-15.20_i386.deb
If I do it through the synaptic do you think it will download the latest version?

Edit:
"NVIDIA binary XFree86 4.x/X.Org 'new' driver 
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and supports the  newer
GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
flat panel displays are also supported."
Does that mean pci-express is also supported? I use pci-express.

Edit:
What's the difference between nvidia-glx and nvidia-glx-new? The restricted drivers manager was trying to download nvidia-glx, that's why the version is 9631. My gfx card is a 6600GT. Should i use the nvidia-glx instead of nvidia-glx-new?

Edit:
Forget it, nvidia-glx-new is not compatible with my system. After I installed it the x server couldn't start again.
Thanks for helping me anyways.

---

### Post by andrew.co.za on 2007-05-07
I've been forum hopping for 4 days now. I finally got the .run file running by turning off the x server but now i'm at the part where it says it's going to compile something because it can't download it (i'm not online at home). Then it brings up the message that libc something or other is missing. How do i fix this???

I've tried clicking around in the package manager, i've tried looking on the ubuntu cd. could someone please tell me how to satisfy the nvidia glx installier so that i can finally enjoy ubuntu and beryl.

Specs:
nForce4 chipset
AMD64 3500+
Gefore 7900GTX
Ubuntu Feisty Fawn
nvidia glx 9755 drivers (.run file)

---

