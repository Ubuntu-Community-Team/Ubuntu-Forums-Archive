---
title: "Help out a total newb with FX5500"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by tc48 on 2006-12-30
Hey Guys,

I am an expert with windows, but have never touched linux before.  I've heard ubuntu is capable of some pretty amazing things so i figured id give it a run.  I installed the OS, and everything moved fluently on the screen, but my res was 1024x768.  My monitor, a Sony SDM-HS73 is capable of 1280 x 1024  with a refresh rate of 60Hz.  My video card is a Nvidia FX5500.  When i go through and change the vesa resolution to 1280x1024 and restart, it displays in 1280x1024, but when you move windows around on the screen they move extremly slowly, and in "pieces" if you will.  Do I need to install certain drivers?  If so how do I do this.  Thanks for your help, I know this is probably 2+2 for you, I'm kind of embaressed haha.

---

### Post by taurus on 2006-12-30
You need to install nVidia driver for your graphic card...

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by tc48 on 2006-12-30
figured.... so i just type

deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/

in the terminal and go from there?

---

### Post by confused57 on 2006-12-30
> **tc48 said:**
> Hey Guys,

I am an expert with windows, but have never touched linux before.  I've heard ubuntu is capable of some pretty amazing things so i figured id give it a run.  I installed the OS, and everything moved fluently on the screen, but my res was 1024x768.  My monitor, a Sony SDM-HS73 is capable of 1280 x 1024  with a refresh rate of 60Hz.  My video card is a Nvidia FX5500.  When i go through and change the vesa resolution to 1280x1024 and restart, it displays in 1280x1024, but when you move windows around on the screen they move extremly slowly, and in "pieces" if you will.  Do I need to install certain drivers?  If so how do I do this.  Thanks for your help, I know this is probably 2+2 for you, I'm kind of embaressed haha.
First I'd change to the "nv" driver...open a terminal(Applications---Accessories---Terminal), enter:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```
this will create a backup file, then:
```
gksudo gedit /etc/X11/xorg.conf
```

scroll down to the video device driver and change the driver from "vesa" to "nv"
save & exit

Then press Ctrl+Alt+Backspace, log back in...if there is no improvement, you may need to reboot.

If for some reason, X doesn't load, you can boot into recovery mode and restore your old xorg.conf file:
```
sudo nano /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```

You can always do it interactively:
```
sudo dpkg-reconfigure xserver-xorg
```

As taurus mention, for optimum performance, you can use the "nvidia" drivers...I have an AGP FX5500 & the "nv" driver works pretty well.

---

### Post by taurus on 2006-12-30
No.  You need to add that line to the end of your /etc/apt/sources.list.  So, open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/apt/sources.list
```
Now, scroll all the way to the end and add that line.

Save it and from the same terminal, run

```
wget http://albertomilone.com/drivers/tseliot.asc
gpg --import tseliot.asc
gpg --export --armor albertomilone@alice.it | sudo apt-key add -
sudo apt-get update
sudo apt-get install linux-generic (if you are using the generic kernel!!!)
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```
Now, restart your X by pressing down <Ctrl><Alt>Backspace.  If everything is working fine, you should see an nVidia logo...

---

### Post by tc48 on 2006-12-30
alright guys  i'm gonna reinstall the os over the one i already messed up.. then do what u said.  I'm runnin to the gym so i'll get back to you in a few hours.. thanks for all your help!

---

### Post by riven0 on 2006-12-30
> **tc48 said:**
> alright guys  i'm gonna reinstall the os over the one i already messed up.. then do what u said.  I'm runnin to the gym so i'll get back to you in a few hours.. thanks for all your help!

Re-install? Why? Just lower your resolution back to 1028x768 and install the official drivers. You'll be up in a jiffy! :D

---

### Post by tc48 on 2006-12-31
ok I followed your instructions... and it semeed like everything installed great.. I went to restart the X and I got this...

> Failed to load module "ufb" (module does not exist, 0)
Error: API mismatch: the NVIDIA kernal module has the version 1.0-8774, but this X module has the version 1.0-9746.  Please make sure that the
kernal
module and all NVIDIA driver components have the same version.

It then went on to tell me to make sure i have an nvidia gpu ect.. any idea where i went wrong?

---

### Post by riven0 on 2006-12-31
> **tc48 said:**
> It then went on to tell me to make sure i have an nvidia gpu ect.. any idea where i went wrong?

Okay, the xserver should spit out a bunch of errors until it boots you into the terminal screen. From there you can revert back. Log in and type:

> sudo nano /etc/X11/xorg.conf

You should find a section similar to this:

> Section "Device"
	Identifier	"Nvidia FX5500"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection


Change the driver to nv so it looks similar to this, (changes in bold):

> Section "Device"
	Identifier	"Nvidia FX5500"
	Driver		**"nv"**
	BusID		"PCI:1:0:0"
EndSection


Now reboot the comp. Hopefully, you'll get the gui back. If not, when you get to the terminal, just do:

> sudo dpkg-reconfigure xserver-xorg and just keep on hitting enter for the defaults. 

Then we can try to figure out the problem.

---

### Post by tc48 on 2006-12-31
well what do you know.. I Went to boot back into ubuntu, and voila NVIDIA Logo and it booted fine now!... If one of you guys dont mind, when you have a chance, can you tell me what exactly all those commands were doing, so I have an understanding of what I did.  And maybe point me in the direction of some basic tutorials on how to use the terminal and install programs?  THanks!!

---

### Post by riven0 on 2006-12-31
> **tc48 said:**
> well what do you know.. I Went to boot back into ubuntu, and voila NVIDIA Logo and it booted fine now!... If one of you guys dont mind, when you have a chance, can you tell me what exactly all those commands were doing, so I have an understanding of what I did.  And maybe point me in the direction of some basic tutorials on how to use the terminal and install programs?  THanks!!

Are you talking about the commands I gave you? :confused:

---

