---
title: "Monitor not working with Ubuntu"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Lollyn00b on 2006-10-24
Hey, I'm new to Ubuntu, and Linux in general (Been using Windows my whole life).  I decided I wanted to try Ubuntu out, so I downloaded the ISO, burned it to a disk, and booted up my computer.  It worked fine, up until it finished loading.  Once it had loaded all the drivers, the screen went black, and a sound played.  What I'm thinking happened is that Ubuntu didn't recognize my monitor.  Any help?  Here are my system specs:

2.6 GHz Pentium 4
1.5 GB RAM
NVidia GeForce 5500FX with 256MB of RAM
1024x768 HP Flatscreen monitor

---

### Post by Xappe on 2006-10-24
what happens if you press ctrl + alt + F1 at the black screen?
(that should get you to a text console)

---

### Post by Lollyn00b on 2006-10-24
When I did that, it said something about me not having the right version of X Window or something.  I'm not sure of the details, but if you need them, I can do it again and write down exactly what it said.

---

### Post by Xappe on 2006-10-24
after the X error message you should be dropped at a console login screen. Login and try 
```
sudo dpkg-reconfigure xserver-xorg
```
(when prompted, use your user password)

Go through the configuration and choose values and settings that you think is suitable for your setup.

When done, do a:

```
sudo /etc/init.d/gdm restart
```

---

### Post by Lollyn00b on 2006-10-24
I never got dropped off at a login screen, but I reconfigured that X window thing, used that second command, and it said that GNOME stopped successfully, but failed to restart.  I've heard that Kubuntu uses KDE (I think) instead of GNOME; should I try that?

---

### Post by nickburns on 2006-10-24
go to the terminal, [alt+ctrl+f1] , log in and type

more /etc/X11/xorg.conf

Copy and post back the sections name "Device" , "Monitor" and "Screen"

they will look something like 

Section "Monitor"
	Identifier	"DELL 1905FP"
	Option		"DPMS"
EndSection

and we will help you through this...

---

### Post by Xappe on 2006-10-24
the problem lies at the xserver config, not the desktop environment, so you should be fine with gnome.

do you have any specifications for your monitor? 

I would like to have a look at your /etc/xorg.conf file and you could write down that X error message too, so we can see if that makes any sense.

You could boot with the livecd, mount your root partition

```

sudo mkdir /mnt/ubuntu_root
sudo mount /dev/<rootpartition> /mnt/ubuntu_root

```

(where <rootpartition> is substituted by your partition, something like hda1 or hdb4, you can find out by running "sudo fdisk -l")

and copy the contents of /mnt/ubuntu_root/etc/X11/xorg.conf here

---

### Post by Lollyn00b on 2006-10-24
I still haven't run into a login screen, so I can't "Log in"... :neutral: 

"more /etc/X11/xorg.conf" Didn't show me what you said it would, but if you needed to know the name of my monitor, it has "hp pavilion f1703" written on it at the bottom.  I haven't tried that "sudo mount /dev/<rootpartition> /mnt/ubuntu_root" thing yet; I'll wait to see if I need to, or if the monitor info helps you any; I'd rather not have to keep restarting my computer if I don't need to @_@.

---

### Post by nickburns on 2006-10-24
Try the:

more /etc/X11/xorg.conf 

again, when it displays the file keep pressing the enter button until you get to the sections for the monitor and your graphics card.  Basically what the problem is, you need to adjust some settings in that xorg file so your monitor can display gnome.

Also, I am a little unclear if you have installed ubuntu or if you are working off of the install cd only.

---

### Post by Xappe on 2006-10-25
> **nickburns said:**
> 
Also, I am a little unclear if you have installed ubuntu or if you are working off of the install cd only.

yeah, I took for granted his system was installed on the computer, but now I can see that it's a bit unclear.

Will do some googling on that monitor though, when I get some free time tonight...

---

### Post by Lollyn00b on 2006-10-25
Oh, sorry for not specifying; I'm running off the CD only; I haven't installed it. I can't, actually; the monitor stops working right after it finishes loading the drivers.  Also, if it helps, I can only access the Ctrl-Alt-F1 thing in safe mode.

---

### Post by nickburns on 2006-10-26
OK, now with this knowledge we will get you going.  We need to get a hold of your xorg.conf file.  A couple options:

try : 
more /etc/X11/xorg.conf 

and copy the 'Device','Monitor' and 'Screen' section

or
sudo cp /etc/X11/xorg.conf /home/xorg.conf.txt

and attach that .txt file to your next post.  I think that we will just need to change a couple lines in that file to get you going...

---

