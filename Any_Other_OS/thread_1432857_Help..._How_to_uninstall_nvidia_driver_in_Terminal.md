---
title: "Help... How to uninstall nvidia driver in Terminal only"
date: 2010-03-18
forum: Any Other OS
---

### Post by merc1973 on 2010-03-18
[SIZE=6]**SOLVED**[/SIZE]
 
Linux Mint 8 Noob question:
 
So everything was runngin beautifully.... and then i was poking around some settings and i decided to download the nVidia driver for my graphics card since none was installed. It prompted me to restart to instanll driver, so i did. And when login screen comes up the monitor shuts off (assumuming that is the time the driver is turned on...) I can run in recovery mode but that is just terminal only.... So my question is how do i "roll back" the driver to the original one pre existing on Linux mint through the command prompts only in recovery mode or root??????
 
I cant even find a nvidai directory..... aahhhhhhhhhh!!!!! [IMG]http://forums.linuxmint.com/images/smilies/icon_surprised.gif[/IMG] 
 
Specs: Dell C840, 2.4 GHz CPU, 1GB Ram, 60 GB HDD, Geforce 4400, Intel internal mini pci wireless card, Linux Mint 8

---

### Post by patchwork on 2010-03-18
```
sudo rmmod nvidia
```will remove the driver module from the kernel

If you are using an xorg.conf (/etc/X11/xorg.conf), 

change Driver "nvidia"

to Driver "nv"
in the Section "Device"

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by merc1973 on 2010-03-18
> **patchwork said:**
> ```
sudo rmmod nvidia
```will remove the driver module from the kernel
 
If you are using an xorg.conf (/etc/X11/xorg.conf), 
 
change Driver "nvidia"
 
to Driver "nv"
in the Section "Device"
 
```
sudo nano /etc/X11/xorg.conf
```
 
 
Tried the first code and did not show any results of removing any files.
 
Sorry, I'. not quite sure what or if i used an xorg configuration????

---

### Post by merc1973 on 2010-03-18
> **patchwork said:**
> ```
sudo rmmod nvidia
```will remove the driver module from the kernel
 
If you are using an xorg.conf (/etc/X11/xorg.conf), 
 
change Driver "nvidia"
 
to Driver "nv"
in the Section "Device"
 
```
sudo nano /etc/X11/xorg.conf
```
 
 
OK, so I'm in /etc/x11/xorg.conf,  (GNU nano 2.0.9)   what do i do next?

---

### Post by patchwork on 2010-03-18
> OK, so I'm in /etc/x11/xorg.conf,  (GNU nano 2.0.9)   what do i do next?

First, make sure that it is /etc/X11/xorg.conf (case-sensitive).

If it is populated (there are entries), go to

Section "Device"

and change

Driver "nvidia"

to 

Drvier "nv"

If the document is blank, you don't need to change or add anything.

Just to check what driver is loaded, you can run 

```
lsmod
```

If you see nvidia in the list, the proprietary nvidia driver is still loaded (it should not be after using the rmmod command in the previous post)

If you see nv in the list, that's a good thing.  (It's the default open source driver for Nvidia video cards).

---

### Post by merc1973 on 2010-03-18
> **patchwork said:**
> First, make sure that it is /etc/X11/xorg.conf (case-sensitive).
 
If it is populated (there are entries), go to
 
Section "Device"
 
and change
 
Driver "nvidia"
 
to 
 
Drvier "nv"
 
If the document is blank, you don't need to change or add anything.
 
 
Just to check what driver is loaded, you can run 
 
```
lsmod
```
 
If you see nvidia in the list, the proprietary nvidia driver is still loaded (it should not be after using the rmmod command in the previous post)
 
If you see nv in the list, that's a good thing. (It's the default open source driver for Nvidia video cards).
 
 
 
:D:D:D:D:D:D
 
I am such a Dumb*ss... I had no idea it was case sensitive....  Thank you all so very much!  followed it perfectly and changed to "nv"...  typical noob i guess.....

---

### Post by krishnasarswat on 2011-05-22
> **patchwork said:**
> ```
sudo rmmod nvidia
```will remove the driver module from the kernel

If you are using an xorg.conf (/etc/X11/xorg.conf), 

change Driver "nvidia"

to Driver "nv"
in the Section "Device"

```
sudo nano /etc/X11/xorg.conf
```



When I Type sudo rmmod nvidia and hit enter, it tells Module nvidia is in use..
what's the solution for it

---

### Post by Livin4Jesus on 2011-08-30
> **krishnasarswat said:**
> When I Type sudo rmmod nvidia and hit enter, it tells Module nvidia is in use..
what's the solution for it

Restart your computer and go to the recovery version of Ubuntu. Look for netboot(?) and use the command from there.

---

