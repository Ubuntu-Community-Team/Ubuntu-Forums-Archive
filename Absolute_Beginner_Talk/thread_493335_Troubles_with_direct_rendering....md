---
title: "Troubles with direct rendering..."
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Tuning_In on 2007-07-05
Hi!

I have the same issue as described here [http://ubuntuforums.org/showthread.php?t=473249&highlight=test+opengl+direct+rendering](http://ubuntuforums.org/showthread.php?t=473249&highlight=test+opengl+direct+rendering)
I have tried to edit the xorg.conf file, but with no luck. I use Kubuntu 7.04 as distro. 

When I run the code: glxinfo | grep direct I get this output

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

My xorg.conf file look like this:

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Got any ideas?

Thanks in advance:)

---

### Post by dfreer on 2007-07-05
You are using the default "nv" driver, and you'll want to use the "nvidia" driver to use direct rendering.

Try doing these commands:
```
sudo apt-get install nvidia-glx-new
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nvidia-xconfig
```

Reboot.
Important thing here is to realize that if upon reboot X server crashes, you can restore the backup with the following command from the terminal (Hit <Ctrl><Alt><F5> if you don't see a login prompt):
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
You might want to write that last part down ;)

If you have further problems with beryl, remember that you'll need to run this command in place of *sudo nvidia-xconfig* (I wouldn't worry about it now unless you plan on running beryl):
```
sudo nvidia-xconfig --add-argb-glx-visuals
```

Good luck and let us know if this fixes things for ya!

---

### Post by Tuning_In on 2007-07-05
Thank you!!! 
That did it\\:D/  Help is much appreciated!

---

