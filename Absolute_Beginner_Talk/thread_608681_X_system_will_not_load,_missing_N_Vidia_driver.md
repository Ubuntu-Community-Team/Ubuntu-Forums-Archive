---
title: "X system will not load, missing N Vidia driver"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Sharkey_Hfx on 2007-11-10
I have just finished installing Ubuntu 7.04 (Fiesty fawn).

I am able to boot from the Live CD and the X system graphical interface appears correctly. It seems to detect and install my NVidia Video card fine. 

However, when I try to boot from the Install I have made to my hard drive, I reveive an error that the X system was unable to start as it could not find the NVidia driver.

I do have the ability to login to through the terminal, but I really haven't learned any Linux command line stuff yet.

I was wondering if someone could help, or point me to information on loading the drivers correctly.

Also I notice that from the live CD it does lock sometimes unless I choose the "safe graphics mode" but I assume this is a drivers issue as well which I can tinker with better once I am working with the "real" install.

Any help would be appreciated!

Thanks!

---

### Post by Tux.Ice on 2007-11-10
Try fixing that from the live cd go to nvidias website and see if they have any linux drivers if they do download them they should be in a tarball go to terminal type

xfcv name-of-tarball.tar.gz

and press enter make sure your in the directory where you downloaded it

---

### Post by infurnus on 2007-11-10
If you just need to get the GUI up go to /etc/X11 edit xorg.conf where you choose nv or nvidia drivers chage it to vesa then run startx again. This will at least get you in to make it easier to download the drivers.

```

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"vesa"
	BusID		"PCI:0:13:0"
EndSection

```

---

### Post by Sharkey_Hfx on 2007-11-10
Nvidia supplies the driver as a .run file (??):
NVIDIA-Linux-x86-96.43.01-pkg1.run

[http://www.nvidia.com/object/linux_display_x86_96.43.01.html](http://www.nvidia.com/object/linux_display_x86_96.43.01.html)

I'm really not that familiar with Linux yet, so I'm not sure exactly what I should be doing.

I just noticed infurnus post to this thread, so I may do as he suggests so I can boot from the install first, and then try loading the drivers

---

### Post by Sharkey_Hfx on 2007-11-10
I was able to get the the x system to load by setting the driver to vesa as suggested by infurnus.

I tried downloading the drivers from the nvidia website. I would try to install this and it would indicate that I was running in a x windows environment.  I booted to a prompt, and it indicated I needed root to install.

Being the linux newbie I am.. I will have to figure that out.. 

I went to the restricted drivers, and allowed the nvidia driver for now.

I did read another post about using Envy to detect and download the drivers, this is my next step when I get home from work.

---

