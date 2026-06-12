---
title: "installing NVIDIA driver"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Aidan James on 2007-08-28
ok, so my upstairs pc has no internet connection wwhatsoever, i have ubuntu on it. i wanted to give the wobbly windows a go, but was told i had to install the driver. so, i downloaded the .run file on my windows pc, transferred it to my usb stick, and loaded it on my upstairs ubuntu pc. i clicked on run in terminal, logged in as root, but was told to kill x. so i pressed ctrl + alt+F1. then i typed in 

sudo/ etc/init.d/gdm stop

sudo sh/ patch/to/package.run

but it said it couln't find the package, whe file is stored on my desktop. is there a way around this-bear in mind my ubuntu pc has no internet access, thanks in advance.

---

### Post by dr.koljan on 2007-08-28
Hi,

If the file is on your desktop, then you should type:

```
cd Desktop
sudo sh NV*
```

Good luck :)

---

### Post by r4ik on 2007-08-28
Try,

cd Desktop

So the installer can find the file not sure if it is going to work if there is no internet.

---

### Post by Aidan James on 2007-08-28
thanks guys, but when i type either of those in the terminal, it says i need to kill x. so, should i press CTRL+ALT+F1 and then type what you said.?

---

### Post by bodhi.zazen on 2007-08-28
Well, you will need more then the nvidia script.

You also need build-essential, xserver-xorg-dev, and the (kernel) headers.

See this link :

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

You need these packages :

> apt-get install linux-headers-`uname -r` build-essential xserver-xorg-dev

**NOTE** Those are back tics ` (on my keyboard near the number 1) not single quotes '

If linux-headers-`uname -r` does not work, you will have to use thsi command :```
uname -r
``` in a terminal and search for the headers in synaptic.

See Aptoncd to transfer the files : [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)


============


OK, once you have all that installed,

Ctrl-Alt-F1 to drop to the terminal

```
sudo /etc/init.d/gdm stop
``` To stop X

sudo sh /path/to/Nvidia_installer #/home/username/Desktop or what have you

=========

You can also look at the envy script, however using the envy script off line may be difficult (same packages to be installed)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

=========

Some will advise you install 

sudo apt-get install nvidia-glx nvidia-settings

nvidia-glx and nvidia-glx-new are the optn source drivers and they may or may not work. If they do not work, they have to be removed before you can install the nvidia driver. nvidia-glx-new does not remove cleanly, ever with the --purge option (it is a bug).

---

