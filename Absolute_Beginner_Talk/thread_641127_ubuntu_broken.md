---
title: "ubuntu broken"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by zostra on 2007-12-15
Hi,

installed gustytwo days back, initially everything worked fine.
I had set it up to automatically log in.
now it shows up with the log-in screen i put in my user name and password,
accepts them and tries to load the desktop but crashes back to the log-in screen.

bear in my i am new user.
Any help would be appreciated.

:)zostra:)

---

### Post by daimaru on 2007-12-15
it is most likely a problem with your xserver, maybe you installed graphics drivers and they are not compatible with your card. to get some feedback. at the login screen hit ctrl+alt+f1 which drops you to terminal. now you can login to your system in text mode. once your in try the command 

```
startx
```if it outputs loads of errors saying that xserver could not be started, its most likely your graphics card driver. since you did not add your hardware in your specs, i can't tell you exactly what to do. the easiest way is to reconfigure your xserver. 
to do this first we're going to backup your old xorg.conf file.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```before we reconfigure xserver, its is probably best if you took a look at your xorg.conf file and located the section where your graphics card driver is configured. look for a section that looks like this one (mine)
```
Section "Device"
    Identifier    "nVidia Corporation G80 [GeForce 8800 GTS]"
    Boardname    "nv"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "Samsung SyncMaster 214T"
```the interesting part is the Driver        "nvidia" thing. if your using nvidia card with restricted drivers this is the right setting if your using nvidia card with the default drivers that came with ubuntu it should say Driver        "nv"
if your using ati its going to be either Driver        "fglrx" or Driver        "ati"
sorry not so sure with the ati, but i think thats what it was. 
I'll assume your using nvidia from now on. adjust to ati if you have ati.
if you broke your xserver by installing new drivers you should probably revert back to the default ones ( nvidia that would be "nv" ati -_> "ati")
now you could just edit your xorg.conf file manually using```
 nano /etc/X11/xorg.conf
```and change the line ("Driver        "nvidia") to read either "nv" or (for ati use "ati") or if nothing like that works go to save mode and enter "vesa". its probably best to try this first after editing your file hit ctrl+x select yes to save file and save it as xorg.conf (default, just hit enter) then restart your xserver by typing 
```
sudo /etc/init.d/gdm restart
```if this did not work do a reconfigure of xserver.

STEP2 (if above did not work)
next reconfigure the xserver. this can be quite overwhelming with questions, so just answer with the defaults for everything you don't have the slightest idea , as to what its supposed to be. the only important part is the one right at the beginning where you are asked to choose your graphic card driver. now if you have a nvidia graphics card, you should choose either nv or nvidia here
```
sudo dpkg-reconfigure xserver-xorg
```um sorry went ranting on there, just try this for now and give some more infos if it did not work.

---

