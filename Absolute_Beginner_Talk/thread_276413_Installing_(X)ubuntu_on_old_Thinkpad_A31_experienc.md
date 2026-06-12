---
title: "Installing (X)ubuntu on old Thinkpad A31 experiences -- questions within"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by brian5588 on 2006-10-12
I'm currently using an relatively old Thinkpad A31, 128mb ram, Pentium 4 M, 20 GB hard drive. I've wiped the hard drive clean, hoping to get a linux system that runs smoothly.

When I try to install off the live xubuntu cd, the GUI lags incredibly to the point that I can't even get the install to work. A friend told me to do a server install and then apt-get install xubuntu-desktop. Is this in any way different from a normal xubuntu install? Is a server install text based?

I'm only choosing xubuntu because I'm afraid KDE or GNOME won't run smoothly on this hardware. Any other general tips would be greatly appreciated.

---

### Post by AndrewB on 2006-10-12
You might want to consider more RAM. 256meg minimum.

Other than that Try out Damn Small Linix [http://damnsmalllinux.org/]("http://damnsmalllinux.org/")

It is very lightweight

---

### Post by jimrz on 2006-10-12
> **brian5588 said:**
> I'm currently using an relatively old Thinkpad A31, 128mb ram, Pentium 4 M, 20 GB hard drive. I've wiped the hard drive clean, hoping to get a linux system that runs smoothly.

When I try to install off the live xubuntu cd, the GUI lags incredibly to the point that I can't even get the install to work. A friend told me to do a server install and then apt-get install xubuntu-desktop. Is this in any way different from a normal xubuntu install? Is a server install text based?

I'm only choosing xubuntu because I'm afraid KDE or GNOME won't run smoothly on this hardware. Any other general tips would be greatly appreciated.

The "live" cd's gui installer does not seem to work out with that level of ram. download the xubuntu "alternate" install .iso. it is text based, but easy enough to follow and will work with your current ram. although I, too, recommend adding ram to get at least 256 and preferably 512+ Mb.

---

### Post by brian5588 on 2006-10-13
This is a really old laptop i just want to get it working while i'm here at school, i have better computers back home. Thanks for the tips, I'll try it out!

---

### Post by junglepeanut on 2006-10-13
Alternative will make magic happen.

---

### Post by K.Mandla on 2006-10-13
> **jimrz said:**
> The "live" cd's gui installer does not seem to work out with that level of ram. download the xubuntu "alternate" install .iso. it is text based, but easy enough to follow and will work with your current ram. although I, too, recommend adding ram to get at least 256 and preferably 512+ Mb.
Ditto that. The alternate installer is the way to go. If that doesn't work out for you, you'll have the option to install a server as well, and install xubuntu-desktop from there.

On the other hand, 128Mb should be plenty to run Xubuntu once installed. I have a Xubuntu laptop that boots to the desktop and only needs 52Mb to get going. I think I've seen memory usage peak at 108Mb after surfing for an hour or two.

Of course, that being said, if you need to open ten programs at once and listen to music while rendering 3D images ... more memory is better.

(One last aside ... [Mom's 300Mhz P-2]("http://www.ubuntuforums.org/showthread.php?t=273061") running Openbox boots to the desktop on only 27Mb ... and I can't figure out why ... :-k )

---

### Post by Quintin Riis on 2006-10-13
> **brian5588 said:**
> I'm currently using an relatively old Thinkpad A31, 128mb ram, Pentium 4 M, 20 GB hard drive. I've wiped the hard drive clean, hoping to get a linux system that runs smoothly.

When I try to install off the live xubuntu cd, the GUI lags incredibly to the point that I can't even get the install to work. A friend told me to do a server install and then apt-get install xubuntu-desktop. Is this in any way different from a normal xubuntu install? Is a server install text based?

I'm only choosing xubuntu because I'm afraid KDE or GNOME won't run smoothly on this hardware. Any other general tips would be greatly appreciated.Relatively old??!  Damn you kids are spoiled these days!!

Make a swap partition.  Install.  Happiness.  

Like so...
```
% dd if=/dev/zero of=/path/to/swap/anywhere/will/work bs=1024 count=262144
% sudo mkswap <file>
% sudo swapop <file>
```

This requires you either make partitions before starting the graphical installer with cfdisk at the command line or you have someplace else for swap, like a USB key.

---

