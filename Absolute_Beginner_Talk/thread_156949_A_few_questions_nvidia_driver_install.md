---
title: "A few questions: nvidia driver install"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by effectu on 2006-04-08
Hi I just installed Ubuntu AMD 64 Bit version, one of my first linux attempts ever, so I'm just getting the hang of it. I've used UNIX in my CS classes on Sun Solaris, so that helps me out somewhat with knowing terminal commands, but I still need to learn alot more. 

Right now my screen resolution is maxed at 1024x768 in the settings, while my LCD should be running at 1280x1024. So I figure maybe the drivers are whats doing it. nVidia just recently released their new linux drivers, so I downloaded the amd 64 bit version then after installing binutils, i tried doing sudo sh <driverfilename>. Sure enough it loaded up a NVIDIA installer in the terminal, but it produces an error:
> 
You apear to be running X server; please exit X before installing...


How should I go about installing these video drivers? The last thing I want to do is screw up my new ubuntu install.

Thanks.

---

### Post by BjornHaland on 2006-04-08
People say the nvidia-glx is all you need, and you won't have to use the downloaded packages from nvidia.

I am not 100 % sure, but that's what they say. Hope you'll find out.

System->Administration->Synaptic Package Administration
Search: 'nvidia-glx'

This is a quote from the nvidia-glx description:
> NVIDIA binary XFree86 4.x/X.Org driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and support the newer
GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
flat panel displays are also supported.

If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
package instead of this one.

To enable the driver, run "sudo nvidia-glx-config enable".

---

### Post by mlind on 2006-04-08
[QUOTE=effectu]Hi I just installed Ubuntu AMD 64 Bit version, one of my first linux attempts ever, so I'm just getting the hang of it. I've used UNIX in my CS classes on Sun Solaris, so that helps me out somewhat with knowing terminal commands, but I still need to learn alot more. 

Right now my screen resolution is maxed at 1024x768 in the settings, while my LCD should be running at 1280x1024. So I figure maybe the drivers are whats doing it. nVidia just recently released their new linux drivers, so I downloaded the amd 64 bit version then after installing binutils, i tried doing sudo sh <driverfilename>. Sure enough it loaded up a NVIDIA installer in the terminal, but it produces an error:


How should I go about installing these video drivers? The last thing I want to do is screw up my new ubuntu install.

Thanks.[/QUOTE]

you need to shutdown Xserver. Go into terminal session by Ctl+Alt+F1, log in
using you username and password. issue command 
```
sudo /etc/init.d/gdm stop
```

then do what instructions say. You have to install linux-source package to
compile the drivers aswell. After compiling the driver, change "nv" to "nvidia" from /etc/X11/xorg.conf
and issue command 
```
sudo /etc/init.d/gdm start
```

---

### Post by effectu on 2006-04-08
I had ubuntu install the nvidia-glx driver and nvidia-settings, and did the command to install it. It worked, and when I restarted it even showed a brief nVidia screen before going to login. Still however, when I go into nvidia-settings there is no option to change resolution, and then in the regular ubuntu screen resolution settings, max is 1024x768. Its not too big of a deal, but things really do look a whole lot better on this monitor at LCD resolution. Any ideas on how to up the resolution? Or might I have to put on the full nvidia driver?

Thanks

---

### Post by BjornHaland on 2006-04-08
You probably have to run the installer again, but don't take my word for it.
Check if there are any other options first.

But:
When you boot the Ubuntu install disk and run the installer, you can select what resolutions you want Ubuntu to run with.

You may have not checked any other resolutions than the defaults, which is:
640x480, 800x600, 1024x768

I'm not sure, but this may be because if you check a higher resolution at that point, some screens may not be able to handle it, and you might receive an 'Out of range' message on your screen, meaning you won't be able to see anything. This is because Ubuntu starts up with the HIGHEST resolution checked. Therefore, this could very well be the problem in your case, provided I understand you right and you want to use higher resolution, but you can't set it higher than 1024x768.

---

### Post by effectu on 2006-04-08
I suspect you are right unfortunately...
I had some issue with this portion in the install. I think I went to 1280x1024 and hit enter/return and unexpectedly it just went to the next screen, never having checked off the resolution. Do you remember exactly what you have to press to check off one of the resolutions on install so I dont screw it up again?

---

### Post by BjornHaland on 2006-04-09
Yes, you have to press 'space', not 'enter', as that will take you to the next screen.
I did the same thing you did once, and had to go back and start over :/

Good luck!

---

### Post by mlind on 2006-04-09
you can add new resolutions later by doing
```

sudo dpkg-reconfigure xserver-xorg

```

accept default values if you don't know their meaning.
Wizard will prompt you about monitor resolutions, select the ones you want.

Then restart X and go to System > Preferences > Screen Resolution
and change to desired resolution.

---

### Post by wylfing on 2006-04-09
**mlind** gave the right advice for adding new screen resolutions. The video driver probably is not limiting you (although you really do want to be using the "real" nVidia driver).

I strongly recommend *against* downloading the driver directly from the nVidia site unless the driver in the Ubuntu repositories does not work for you for some strange reason. I'd say the best course of action is:

[LIST=1]
[*]Press Ctrl-Alt-F1 and then log in.
[*]If you've previously installed the driver from the nVidia site, go to the installer and re-run it with the [FONT="Courier New"]--uninstall[/FONT] option.
[*]Run this command to stop X:```
sudo killall gdm
```
[*]Run this command to reconfigure X and get a clean xorg.conf:```
sudo dpkg-reconfigure xserver-xorg
```
[*]Run this command to install the nVidia driver from the Ubuntu repositories:```
sudo apt-get install nvidia-glx
```
[*]Run this command to configure X properly for the nVidia driver:```
sudo nvidia-xconfig
```
[*]Reboot.
[/LIST]

---

### Post by geek.de.nz on 2006-08-24
How did you get binutils installed? I just recently got a new computer (AM2 Asus Motherboard with NVIDIA Chipset, NVIDIA LAN etc).

I cannot get the driver installed which is on the Asus CD. It first complained that the binutils package is not installed. Then I checked and there is a package installed called binutils-static. I thought that would do until I get at least my LAN card working, but it didn't. Then I made a symbolic link (/bin/ld) to /bin/ld_static but that gave me a different error:

```

ERROR: Unable to find the system utility 'objcopy'; please make sure you have the package 'binutils' installed. If you do have binutils installed, then please check that 'objcopy' is in your PATH.

          OK

```

However, I cannot find the file 'objcopy' or even a similarly called one anywhere (# updatedb; locate objcopy).

I would really like to run the 64 bit version on this machine. I will still install the 32 bit version for now, but since Windows Vista is coming out as 64 bit version soon, Linux needs some better support for 64 bit architechtures. :-)

---

