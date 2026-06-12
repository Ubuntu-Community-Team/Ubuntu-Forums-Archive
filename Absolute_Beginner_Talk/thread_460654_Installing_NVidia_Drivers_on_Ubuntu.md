---
title: "Installing NVidia Drivers on Ubuntu"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by anim on 2007-05-31
I need help installing the drivers for my NVidia 8600 GTS. They are in a beta release located [here]("http://www.nvidia.com/object/linux_display_ia32_100.14.06.html").

However,  I started to realize i was in over my head when I couldn't get a report on my version of XOrg or XFree86 as [instructed in their readme]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.06/README/chapter-02.html").

My specific questions are do I need to install XFree86 - I don't recognize this one.
and second - why isn't XOrg reporting its version?? I thought XOrg was one of the cornerstones of the whole Linux experience.

I'm entering the console commands verbatim from the instructions on the readme, the first one worked fine but the second one, whether inputted as a whole with the / in it or as seperate commands fails to work.

---

### Post by scrooge_74 on 2007-05-31
try this [http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

---

### Post by anim on 2007-05-31
The reason I ask if I need XFree86 is because I don't know if the console just isn't reporting that I do have it because I messed up or if I really do need to find it and install it for the first time.

This is a brand new installation of ubuntu.

---

### Post by anim on 2007-05-31
I'm going to need a bit more help that that. Just input that directly into terminal?

---

### Post by anim on 2007-05-31
I'm also running fiesty fawn so that link wouldn't be much help.

---

### Post by qamelian on 2007-05-31
> **anim said:**
> The reason I ask if I need XFree86 is because I don't know if the console just isn't reporting that I do have it because I messed up or if I really do need to find it and install it for the first time.

This is a brand new installation of ubuntu.

You don't need XFree86. XFree86 has been replaced by Xorg in most modern distros.

---

### Post by Patrick K on 2007-06-01
Here is the one you can use:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Also, have you tried the restricted drivers applet in the administration menu?

---

### Post by Nythain on 2007-06-01
or you could just open up a terminal and type
```

sudo apt-get install nvidia-glx-new

```
and possibly edit your xorg.conf file
```

gksudo gedit /etc/X11/xorg.conf

```
and make sure that the section that looks like this
```

Section "Device"
    Identifier     "whatever"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:12:0"
    Screen          0
EndSection

```
says Driver "nvidia" and not "nv" or "vesa" or "vga"
you could also, after installing nvidia-glx-new try running
```

gksudo nvidia-settings

```
and making your changes there, remembering to save changes and restarting X with Ctrl+Alt+Backspace

hope any of that was helpfull

---

### Post by Mr Steve Gnarly on 2007-06-01
I have just tried sudo apt-get install nvidia-glx-new but get the following error?

sgnarly@suicide:~$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nvidia-glx-new

can anyone help me work out why ?

sudo apt-get install nvidia-glx works fine but the last time i installed only a matter of weeks ago i used the nvidia-glx-new and it set all my screen res and everything correctly somthing that the nvidia-glx does not do :(

---

### Post by Nythain on 2007-06-01
what does your /etc/apt/sources.list file look like???

---

### Post by Mr Steve Gnarly on 2007-06-01
Here is a copy of my /etc/apt/sources.list.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse

thanks for any help you can give :)

---

### Post by mendingo84 on 2007-06-01
Hey,

Go to that alberto millone site, download that envy file. After that CTRL+ALT+F1, after that, login with USER+Passwd, and after that type envy. And Voila!

---

### Post by Abandon on 2007-06-01
> **anim said:**
> I need help installing the drivers for my NVidia 8600 GTS. They are in a beta release located [here]("http://www.nvidia.com/object/linux_display_ia32_100.14.06.html").

However,  I started to realize i was in over my head when I couldn't get a report on my version of XOrg or XFree86 as [instructed in their readme]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.06/README/chapter-02.html").

My specific questions are do I need to install XFree86 - I don't recognize this one.
and second - why isn't XOrg reporting its version?? I thought XOrg was one of the cornerstones of the whole Linux experience.

I'm entering the console commands verbatim from the instructions on the readme, the first one worked fine but the second one, whether inputted as a whole with the / in it or as seperate commands fails to work.

There is not yet an official linux driver for that card so you need to work with the beta from nvidia. You need to install that driver with:

sudo /etc/init.d/gdm stop
cd to the map with that driver
sudo sh ./NVIDIA-Linux-x86...

Before that you need: sudo apt-get install build-essential and you need to install the kernel headers.
Good luck!

---

### Post by Mr Steve Gnarly on 2007-06-01
> **mendingo84 said:**
> Hey,

Go to that alberto millone site, download that envy file. After that CTRL+ALT+F1, after that, login with USER+Passwd, and after that type envy. And Voila!

Thanks for that but...

I cant get the files to download not even with the terminal (wget) there seems to be a problem on the site [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I dont think i need to install somthing to do this though I know what i need to enter to get my card going (sudo apt-get install nvidia-glx-new) it just wont find it and install it :(

I have just tried the code on another computer (sudo apt-get install nvidia-glx-new) and get the same error has the package been removed/renamed or is it just me?

---

### Post by HemiGTX on 2007-06-01
I dont know if this will help you.. as Im very new to ubuntu myself.. I have an old Geforce4 MX 440 and in my effeorts to install drivers for this card I found this and it worked out great:

```
http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/
```

The Process:

   1. Open a terminal and type sudo apt-get update
   2. Type sudo apt-get install nvidia-glx
   3. Type sudo apt-get upgrade
   4. Type sudo dpkg-reconfigure xserver-xorg
          * Select the nvidia driver from the X server driver list and follow the on-screen steps to complete the configuration
   5. Once finished with the configuration, hold down Ctrl+Alt+Backspace to restart X server. You should be presented with a nice NVIDIA splash screen signaling that the driver is installed and working
   6. You can test this in the terminal by typing glxinfo | grep direct (the output should be direct rendering: yes)
   7. You can also type glxgears to watch your card at work

---

### Post by Mr Steve Gnarly on 2007-06-01
That is basicaly what i have done to get mime working at the moment but..
The screen res only goes up to 1024X768 and I have noticable flickering in the screen image from time to time. This is how it was befor until i found the nvidia-glx-new. 
Once i had installed that everything was sorted automaticaly.

Its driving me nuts having the screen set to 1024X768 everything is masive...
If i could fix that problem only i would be a lot happy'er. I dont play games or anything like that so the odd flicker isnt that much of a problem I just know it would be fine if i could get the nvidia-glx-new package AAARRRRR!!!

BTW Thanks for everyones help so far...

---

