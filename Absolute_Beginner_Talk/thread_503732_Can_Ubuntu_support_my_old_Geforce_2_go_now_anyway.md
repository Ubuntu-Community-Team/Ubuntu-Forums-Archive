---
title: "Can Ubuntu support my old Geforce 2 go now anyway?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by kasperl on 2007-07-18
Need not say that i am a newbie here
i am running Ubuntu on my rather old notebook,older than 5 years
but i have updated it to 512M ram, so it isn't doing its job too bad
but i found that the driver for its video card(Geforce 2 go) doesn't work well
whenever I drag a windows, i can see that clearly, too clearly...
so u can imagine when i try clicking the menu item "Screen Effect" in "System/Preference"
and then Ubuntu told me it will install a new driver for my video card to work better for 3D effects
I was rather happy of coz
but after that was done and i restarted my notebook
I only got a black screen...
I have search for this problem in ubuntu website
and found that it has been reported about a year ago that some Nvidia card's driver have this problem
i don't know why ubuntu keeps auto-install driver which is known to be imperfect

In whole i rather like Ubuntu, but i still can't find a proper driver for my video card,even in Nvidia's official website
pity

---

### Post by GeeZor on 2007-07-18
login as root and try the following:
```

apt-cache search nvidia 
```

somewhere there should be a line that says nvidia-glx-legacy or something. The legacy package you need to install for support for older NVIDIA cards. Google around for nvidia-glx and nvidia-glx-legacy to obtain a list of supported cards, but hyours should be in one of those lists.

install the package like so: (as root )
```

apt-get install nvidia-glx
apt-get install nvidia-glx-legacy

```

Should do the trick. 
After that make sure your /etc/X11/xorg.conf file also uses your new driver module, using apt that should be done for you so no worries. 

Good luck and let me know how things work out.

GeeZor

---

### Post by kasperl on 2007-07-18
well, i have typed the command below:
sudo apt-get install nvidia-glx-legacy
the it installed nvidia-glx-legacy_1.0.7184+2.6.20.5-16.29_i386.deb for me
i am not sure if it is right, because i have check the list of supported nvidia cards here
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)
and it says my Geforce2 Go should be supported by 1.0-96xx driver
and after the installation, the file /etc/X11/xorg.conf don't change at all
the section about video card runs as follow:

Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 Go]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

is there anything wrong?

---

### Post by GeeZor on 2007-07-18
nope, nothing is wrong.

do this:
```
 
lsmod | grep nv 
```

it should either nv or nvidia.. both are kernel modules (drivers)
nv is a default dirver that almost always works. 
if lsmod also finds an nvidia, substitute nv in the xorg.conf with nvidia and restart x  (startx from a shell as user)

if that fails try this:
```

modprobe nvidia

```
look here aswell : [http://tldp.org/HOWTO/Module-HOWTO/x197.html](http://tldp.org/HOWTO/Module-HOWTO/x197.html)

l

---

### Post by kasperl on 2007-07-19
err...
i've got a black screen again-_-
have tried both nvidia-glx and nvidia-glx-legacy
and have added  [COLOR="Red"]Option "UseDisplayDevice" "DFP" [/COLOR] to xorg.conf
i have to change nvidia to nv in xorg.conf in order to see XWindows now

---

### Post by kasperl on 2007-07-19
well,i've got a very funny problem
after i have typed the commands as follows:
  [COLOR="Red"]apt-get install nvidia-glx
  nvidia-xconfig
[/COLOR]
then i press ctrl+alt+backspace to restart XWindow
after i did this,i found the driver worked well,and the screen effect could be enabled
i thought all my problems were solved
but...after i reboot my notebook
black screen again

So if I only restart XWindow after installing nvidia-glx,everything is ok
but not after I reboot my notebook...
somebody help me,plz

---

### Post by kasperl on 2007-07-19
well,i've found a kind of solution to this problem
every time after I power on my notebook,and get a black screen
just press ctrl+alt+backspace to restart XWindows
then I will get screen output...
it is a little annoying of course, but at least I can play some video with my ubuntu now...
thanks to all that have been helping me

---

