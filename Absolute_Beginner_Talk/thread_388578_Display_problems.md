---
title: "Display problems"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Danoob on 2007-03-19
Well I'm a complete newb to linux.  

When I boot from the live cd, i get to desktop and it's all distorted.  I was able to boot doing 
F6 and removing splash and quite and adding vga=. Everything works ok there.  I'm trying to install it now, which I can do from live cd, but when it boots off hard drive i get distorted login.  I can see enough to log myself in, then back to desktop which is usuallly black and white lines.  

I'm guessing it's a video card driver issue, but I have had no luck with some of the fixes i've tried.  I guess I have to install the driver from command prompt because I cant get the GUI to work unless it's off live cd. I've seen some guides to installing drivers,but they usually are done within GNOME and have updates from universe.

My video card is nvidia 7800gs agp, processor amd64.

Any ideas where to start? 

Thanks in advance

---

### Post by Kobalt on 2007-03-19
It could be a driver issue but also a mistyping error : did you add simple " vga= " or did you add " vga=771 " ? Knowing the second choice is the right one...
If it's a driver problem : once you get to the login screen, press Ctrl+Alt+F1 to access a command line. Log in from there with your user name and password and type ```
sudo dpkg-reconfigure xserver-xorg
```
This will get you to the tool to reconfigure your graphic card drivers : select "vesa", those drivers work 99% of the times. Reboot your computer and if the display is quite normal (I don't talk about resolution that might be low) go on installing the [nVidia drivers]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper").

---

### Post by schwascore on 2007-03-19
I don't know if this will fix your situation, but to install the most up-to-date drivers from NVIDIA from the command line, do the following:

```

sudo apt-get install linux-headers-`uname -r`

#For 32-Bit Install
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run

# For 64-Bit Install
wget ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run

chmod 755 NVIDIA*
sudo /etc/init.d/gdm stop

#For 32-Bit Install
sudo ./NVIDIA-Linux-x86-1.0-9755-pkg1.run

#For 64-Bit Install
sudo ./NVIDIA-Linux-ia64-1.0-5336-pkg1.run

```

Do not have the installer download anything, just have it compile a new kernel module and enjoy your shiny new NVIDIA drivers

---

