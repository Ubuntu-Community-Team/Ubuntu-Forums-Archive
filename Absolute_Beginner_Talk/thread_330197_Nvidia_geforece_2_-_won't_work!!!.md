---
title: "Nvidia geforece 2 - won't work!!!"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-01-02
Hello

I have a geforce2 installed (32MB AGP)

When I first started using Ubuntu it worked fine. However, because of the complex nature of linux when it comes to new people, something got changed in the configuration and now it does not work. It boots up fine to the desktop, but no 3d games, or even screensavers with OpenGL will work. Its like the hardware acceleration isn't enabled anymore.

I've tried uninstalling the legacy drivers, then reinstalling them. the "nv" driver is listed in my xorg.conf file. I see no reason for it to have changed, but yet it has. When I first installed ubuntu and the legacy NVidia drivers, all the 3d games and screensavers worked. Now they don't

can anyone help me out??

thanks,
Jon

---

### Post by ingo on 2007-01-03
> because of the complex nature of linux when it comes to new people, something got changed in the configuration and now it does not work

While this conveys a sentiment we all know to well it really does not give anybody anything to go on. What exactly did you do to make it stop work? Some update? Have you tried any other NVidia drivers? 

If unsure how to do so simply search the forum or have a look here [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) - I found it relatively straight forward to use.

---

### Post by Efwis on 2007-01-03
I also run a GeForce2 gfx card. I found that you don't have to use the legacy drivers. to get it to work do the following.

in synaptic remove the legacy drivers, and install the nvidia-glx drivers, then open termina and do the following:

```
sudo gedit /etc/X11/xorg.conf
```

This will open your xorg.conf file, next find this line
```

	Driver		"nv"
	
```
make it as follows
```

	Driver		"nvidia"
	
```
save the file, and restart gnome.
ctrl+alt+F1 login in, type the following Hitting enter after each line:
```

sudo killall gdm
sudo gdm restart
```

The help files are actually wrong, and they should be changed. This will get your 3d graphics working.

---

