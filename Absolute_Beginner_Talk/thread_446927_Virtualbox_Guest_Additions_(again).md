---
title: "Virtualbox Guest Additions (again)"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by zabyss on 2007-05-17
First, I have to apologize.  I've been searching and there are several threads on this topic, but none are helping.  I'm completely new to Linux and there is a learning curve.  I already posted this on another thread ([http://ubuntuforums.org/showthread.php?t=400205](http://ubuntuforums.org/showthread.php?t=400205)) but I didn't think it would get as much traffic.  Essentially I'm having the same problem that the individual in this thread ([http://ubuntuforums.org/showthread.php?t=402186](http://ubuntuforums.org/showthread.php?t=402186)).  

I have a installed Ubuntu Studio 7.04 via Virtualbox on my Windows XP laptop.  I'm stuck at the 1024x768 resolution which I find extremely counterproductive.  This isn't 1995 after all...  I need to install the guest additions, but I'm having trouble.  I've got the .iso mounted, and it shows on the Ubuntu desktop.  I can't open the files or get it running in any way.  I tried the commands suggested in the aforementioned thread ([http://ubuntuforums.org/showthread.php?t=402186](http://ubuntuforums.org/showthread.php?t=402186)) but to no avail.  It keeps telling me it cannot open the file.  I did once get it to prompt me for my password but it said the same thing, and now I can't get that even.  I know I'm doing something wrong here because I don't know how Linux works.  ](*,)  I really kinda need this spelled out.

Can anyone give me a hand?  I would really appreciate it!

---

### Post by bodhi.zazen on 2007-05-17
> **zabyss said:**
> First, I have to apologize.  I've been searching and there are several threads on this topic, but none are helping.  I'm completely new to Linux and there is a learning curve.  I already posted this on another thread ([http://ubuntuforums.org/showthread.php?t=400205](http://ubuntuforums.org/showthread.php?t=400205)) but I didn't think it would get as much traffic.  Essentially I'm having the same problem that the individual in this thread ([http://ubuntuforums.org/showthread.php?t=402186](http://ubuntuforums.org/showthread.php?t=402186)).  

I have a installed Ubuntu Studio 7.04 via Virtualbox on my Windows XP laptop.  I'm stuck at the 1024x768 resolution which I find extremely counterproductive.  This isn't 1995 after all...  I need to install the guest additions, but I'm having trouble.  I've got the .iso mounted, and it shows on the Ubuntu desktop.  I can't open the files or get it running in any way.  I tried the commands suggested in the aforementioned thread ([http://ubuntuforums.org/showthread.php?t=402186](http://ubuntuforums.org/showthread.php?t=402186)) but to no avail.  It keeps telling me it cannot open the file.  I did once get it to prompt me for my password but it said the same thing, and now I can't get that even.  I know I'm doing something wrong here because I don't know how Linux works.  ](*,)  I really kinda need this spelled out.

Can anyone give me a hand?  I would really appreciate it!

Yea, I had this problem as well.

I solved it by copying the contents of the iso to another location and running the script from there.

The way I did it was to copy the files to a usb drive and I mount and run the install from a USB device (it is much easier).

If the iso is mounted on the Ubutnu guest, copy the files to your home folder and run the install script from there.


```
mkdir ~/addons
cd addons
sudo cp /media/cdrom/* .
sudo chmod a+x VBoxLinuxAdditions.run
sudo sh VBoxLinuxAdditions.run all
```


Since you are on a windows host it might be a little harder to mount the iso.

You can install deamon tools or some such on windows, mount the iso on a virtual CD, and away you go.

One "advantage" of linux is you can mount the iso directly. To do this, copy the iso to a usb and mount it on Ubutnu. Like this :

[http://doc.gwos.org/index.php/VirtualBox#Alternate_Method](http://doc.gwos.org/index.php/VirtualBox#Alternate_Method)

---

### Post by zabyss on 2007-05-17
Thanks very much.  It started to work, but I am getting this after it starts to install:

VirtualBox 1.3.8 Guest Additions installation
Please install the build and header files for your current Linux kernel.
The current kernel version is 2.6.20-15-lowlatency
Problems were found which would prevent the Guest Additions from installing.
Please correct these problems and try again.

I don´t know what these problems might be...

---

### Post by bodhi.zazen on 2007-05-19
> **zabyss said:**
> Thanks very much.  It started to work, but I am getting this after it starts to install:

VirtualBox 1.3.8 Guest Additions installation
Please install the build and header files for your current Linux kernel.
The current kernel version is 2.6.20-15-lowlatency
Problems were found which would prevent the Guest Additions from installing.
Please correct these problems and try again.

I don´t know what these problems might be...

LOL

You just need a little more stuff :)

Install the following on your Ubuntu Guest :

```
sudo aptitude install build-essential linux-headers-`uname -r`
```

The re-try the Additions, you should be fine :)

---

### Post by zabyss on 2007-05-20
Ahhh I owe you one, everything works great.  I can't thank you enough!  :D


> **bodhi.zazen said:**
> LOL

You just need a little more stuff :)

Install the following on your Ubuntu Guest :

```
sudo aptitude install build-essential kernel-header-`uname -r`
```

The re-try the Additions, you should be fine :)

---

### Post by BadSquishy on 2007-06-01
Took me a minute to figure this one out.  When I pasted the command above into my terminal I was getting an error in aptitude:
```
Couldn't find package whose name or description matched "kernel-headers-2.6.20-16-lowlatency"
```
I fired up aptitude's ncurses interface and poked around the "not installed" packages and found the correct package.  

It turns out the package is not called "kernel-header" it is called "linux-headers".  I think the command above needs to be modified to this: 
```
sudo aptitude install build-essential linux-headers-`uname -r`
```

Helpfully Yours,

---

### Post by bodhi.zazen on 2007-06-01
Fixed :)

---

### Post by kehan on 2008-06-04
Thanks worked for me too - now I can get rid of parallels and vmware fusion

---

