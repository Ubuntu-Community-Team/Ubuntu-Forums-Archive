---
title: "Trying to install driver"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Uberuntu on 2007-11-18
ok so i am a complete noob at linux and this is gonna sound like a REALLY dumb question but here goes; i am trying to install my ATI graphics driver and im trying to follow a guide in another thread, but i cant figure out how to type in which directory its in. I have used windows my entire life and in this case the dir would be c:\home\dan\quarentine\internet downloads\then the file. how should i type that into the terminal cuz its saying that no dir exists when i type; /home/dan/quarentine/internet downloads

---

### Post by Qwerty_ on 2007-11-18
I would try the restricted drivers first.

System>Administration>Restricted Drivers manager.

Make sure you have enabled all the repos bar the source.

System>Administration>Software Sources.

---

### Post by Uberuntu on 2007-11-18
ok when i go into the restricted drivers manager the only thing shown says: ATI accelerated graphics driver and its enabled

---

### Post by Uberuntu on 2007-11-18
i am trying to install the driver and the catalyst control center at the same time

---

### Post by ddrichardson on 2007-11-18
What guide are you following? From what I've read the restricted driver is much the same as the latest ATI driver. If you need it though, it's [here]("http://ati.amd.com/support/driver.html"). Or there's [envy]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by tyggna1 on 2007-11-18
For someone who's completely new, you're gonna wanna learn about the following things:


> apt-get (aptitude)
> modprobe -i
> and editing xorg.conf (video card drivers only)


These will be a whole lot more useful than downloading something manually and attempting to install.
All these are commands/files that you can access from the command line.  You can get there from Applications ->accessories -> terminal, or by pressing ctrl-alt-F1 (alt-F7 brings you back to the graphic area)

apt-get automatically downloads and installs software.  in the case for the ATI driver, it can download that package and install it right where it needs to be.  e.g.  ```
sudo apt-get install radeon
```.

```
modprobe
``` 
modprobe is used to install and activate drivers.   Linux doesn't work like windows--Linux loads all the drivers on startup and keeps them loaded.   Windows will constantly bounce drivers off and on your hard drive--according to need.  modprobe -i will install a driver, and you can tell your kernel which drivers to not load either by removing them (modprobe -r <name>) or by editing a file under ```
/etc/init.d/blacklist
```   Just type the name in black list, and Linux won't load any driver whose name appears there.

Lastly, since you're fiddling with graphic drivers, back up /etc/X11/xorg.conf before you do anything else, that way--if you break your gui, you can repair it from the command line by copying the back up over--or by typing in ```
sudo dpkg-reconfigure xserver-xorg
``` to set it back to the way it was when you first installed.   From there, edit the section named "device" to include the name of the driver you want.   Also, if you type ```
man drivername
``` in the terminal--it'll give you a list of Options that you can add to xorg.conf to tweak the way the graphics card works.

Check out my[ zine]("http://ubuntuforums.org/showthread.php?t=542431"), under the article video drivers, driving games for more detailed info.

---

