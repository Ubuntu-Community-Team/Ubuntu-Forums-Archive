---
title: "Maverick on Macbook Pro 6,2 boots to CLI"
date: 2011-01-13
forum: Apple Hardware Users
---

### Post by bradpowers on 2011-01-13
After updating the NVidia Driver to the recommended one.  What's going on?  And how do I get my precious GUI back?

Thanks,
Bradley Powers

---

### Post by bradpowers on 2011-01-14
So, does anybody know why the "restricted" nvidia driver might cause Ubuntu directly to CLI instead of the GUI?  I've reinstalled Ubuntu, which resolved the issue, but I'd like to install the nvidia driver as I'd like for it to work properly.  Sorry for not giving any detail last night, I was frustrated, grumpy, and not thinking straight.  


Thanks,
Bradley Powers

---

### Post by sudo_0 on 2011-01-14
> **bradpowers said:**
>   Sorry for not giving any detail last night, I was frustrated, grumpy, and not thinking straight.  


why were you grumpy? 


did you get it working before posting?

sudo info-get iamconfused OP

---

### Post by bradpowers on 2011-01-14
I was grumpy because Ubuntu would only boot to the CLI, and I couldn't figure out why!

I reinstalled Ubuntu, and didn't install the Nvidia driver.  At the moment it's working in the sense that I'm not booting to CLI, but I'd like to use the Nvidia driver if possible.  


Password:

;)

---

### Post by bradpowers on 2011-01-17
Does anyone have any ideas?  I need to be able to use the NVIDIA driver for what I'm doing, but I also can't operate only in the CLI.  It'd be really great if somebody had any recommendation.

---

### Post by ZeroLinux on 2011-01-18
What is happening when you type gdm and press enter?
Did you try 
```

$ sudo dpkg-reconfigure xserver-xorg 

```
select "nv" for the first screen and hit enter until it's done.

You can also try:
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```

You can try to install new driver this way (I mean you use x86 architecture): (You can take right driver for wget [here]("http://www.nvidia.com/object/unix.html"))

```

mkdir nvidia
cd nvidia
wget http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run
sudo apt-get install build-essential pkg-config
sudo chmod a+x NVIDIA-Linux-x86-260.19.29.run
sudo sh NVIDIA-Linux-x86-260.19.29.run

```

reboot from terminal you can do this way 
```
sudo shutdown -r now
```

---

### Post by _mario_ on 2011-01-19
> **ZeroLinux said:**
> 
You can also try:
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```


don't try that. first, the nvidia driver packages are called nvidia-96, nvidia-173, nvidia-current. and as of lucid, there are no restricted modules packages anymore due to usage of DKMS. hence, the op should install:
```

sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

```

> **ZeroLinux said:**
> 
You can try to install new driver this way (I mean you use x86 architecture): (You can take right driver for wget [here]("http://www.nvidia.com/object/unix.html"))

```

mkdir nvidia
cd nvidia
wget http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run
sudo apt-get install build-essential pkg-config
sudo chmod a+x NVIDIA-Linux-x86-260.19.29.run
sudo sh NVIDIA-Linux-x86-260.19.29.run

```

reboot from terminal you can do this way 
```
sudo shutdown -r now
```


don't try that either. if you really need newer drivers, use the [x-updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").

however, one might need to configure the X server to use the right driver by either running nvidia-xconfig or, since a recent Xorg is capable of configuring almost all devices on its own, it's also feasible to use the configuration file attached (unpack and copy to /etc/X11/xorg.conf), which simply allows to select the driver.

ciao,
Mario

---

### Post by _mario_ on 2011-01-19
... posted twice ... and attachments don't seem to work ...

the xorg.conf file mentioned should contain this:
```

# Xorg configuration to select which nvidia driver is being used

Section "Device"
	Identifier	"NvidiaDevice"

#	# old open-source driver
#	Driver		"nv"

#	# new open-source driver
#	Driver		"nouveau"

	# Nvidia's proprietary driver
	Driver		"nvidia"
#	Option		"RegistryDwords" "EnableBrightnessControl=1"
EndSection

# ***** end of source *****

```

---

### Post by labonny on 2011-02-07
Hey bradpowers - 

Just wondering if you got it working. I have the same setup with a NVIDIA Ge Force GT 330M. I could not get my external monitor (connected via minidisplay port) working at full resolution with the default non-proprietary drivers. 

I installed the proprietary driver (version 260.19.29) from nVidia using pretty much what ZeroLinux said in his wget option, but I had to follow these directions to get it working:
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

So my external monitor now worked at full resolution, but 3D applications (even glxinfo / glxgears) didn't work after this. I just upgraded the drivers from nVidia again using this manual method to version 260.19.36. Now the external monitor and 3D applications both work fine.

I think mario's method using the_[COLOR=Black] [ x-updates PPA]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates?field.series_filter=maverick")[/COLOR]_ should be more reliable, though it looks like they are working off a beta version of the graphics driver - 270.18. I haven't tried this, have you?

best of luck!

---

### Post by Splooshie123 on 2012-03-12
I have the same model with Lucid running. Installing the nvidia driver didn't affect me. So maybe its a problem with Maverick?

---

