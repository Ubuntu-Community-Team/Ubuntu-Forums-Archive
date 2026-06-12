---
title: "X Server Screen error"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by pluckcitizen on 2007-08-22
Hello, I am pretty new to ubuntu (not even sure what version I'm using). My ultimate goal is to resize my windows partition and create a linux ext and swap partitions so i can dual boot my PC into either OS.

The easiest way I found how to do this was through the installation off of the Live CD.

However, when I try to reboot with the live CD, I eventually get the error that "Screens were found but none were in usable configuration" and therefore my x server is all messed up. I think I may know the source of this problem but I do not know how to solve it.

I used to have a intergrated graphics chip in my CPU, but that is currectly disabled and replaced with a NVIDIA Geforce FX 5200 pci card. I feel like the xserver is trying to access the integrated chip when it is not there. 

I've the command "sudo dpkg-reconfigure xserver-xorg" but i feel like it doesnt save the changes i make to it.

I've also searched the forum for solutions, and I've found threads with similar problems but none had a real specific solution.

Also, the alternate installation cd is out of the question for me, because I feel as though even if I get ubuntu installed, it still might not work due to my graphics setup, therefore i want to be positive that it can run graphically before I install it.

Also, the safe graphics option off the cd incurs the same error.

So my question is, is can i configure my xserver to accept the NVIDIA card so I can start up the live cd?

---

### Post by w4ett on 2007-08-22
use the code:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select 'vesa" as the driver, save, then type:

```
startx
```

---

### Post by pluckcitizen on 2007-08-22
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This code does not give me the option to select the driver and only says  that the xserver-xorg was overwritten.

I've tried to selecting the vesa driver through ```
sudo dpkg-reconfigure xserver-xorg
``` but i still receive the same error when i startx

---

### Post by w4ett on 2007-08-22
The up and down cursor keys will scroll through the selection <spacebar> selects and <enter> confirms selections.  the -phigh toggle in the command enables only the video driver and resolution selections and does not affect the keyboard, mouse ...etc settings..in other words it does a minimal reconfiguration of xorg.conf.

---

### Post by pluckcitizen on 2007-08-22
I'm saying that that code takes me right back to the command line, and does not let me choose any configuration options, with or without the cursor keys, etc. However, I am able to get into the configuration through the command without the -phigh toggle.

---

### Post by Arthur Archnix on 2007-08-22
Do you have access to the internet? If so do this:
```
sudo gedit /etc/apt/sources.list
```
A window pops up, put # in front of your cd deb. Save and close. Then
```
sudo apt-get update
sudo apt-get upgrade
```
We can probably bypass all this xorg nonsense if we could just enable your restricted nvidia drivers. Unfortunately, you need the desktop to do that easily. So, the best I can say is to do this:
```
sudo apt-get install nvidia-glx
startx
```
Any luck?

---

### Post by pluckcitizen on 2007-08-22
```
gksudo gedit /etc/apt/sources.list
```

This code says that it "cannot open display"

after I put in the code bleow, it gets something but when I startx I get the same error.

```
sudo apt-get install nvidia-glx
```

---

### Post by Arthur Archnix on 2007-08-22
My bad. Command fixed. Try again. And then post the output of ```
lsmod
```
We may need to load the nvidia module. Anyone know the name of it?

---

### Post by pluckcitizen on 2007-08-22
I do not believe I get internet access during the live boot.

```
sudo gedit /etc/apt/sources.list
```

This code still cannot open display. I also cannot resolve to 'security.ubuntu.com'

any other ideas?

---

### Post by Arthur Archnix on 2007-08-22
Are you using wireless? If so plug it into the lan. Otherwise, I didn't realize you were using a live cd, so I'm pretty sure most of what I said is irrelevant.

---

### Post by pluckcitizen on 2007-08-22
Yeah, I'm on a college campus and all I have is one ethernet port (no routers allowed). It's a pretty secure connection and requires a bit of tinkering in the network management to get it to run right. It appears that it doesnt connect fully during the boot.

---

### Post by pluckcitizen on 2007-08-22
Good news! I got it to boot up by configuring the xserver-xorg! Are there any long term precautions I should make so that this does not happen again?

---

