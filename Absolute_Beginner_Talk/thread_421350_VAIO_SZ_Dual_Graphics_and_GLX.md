---
title: "VAIO SZ: Dual Graphics and GLX"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Khan of Khronos on 2007-04-24
I'm trying to set up Feisty on my laptop, a VAIO SZ. If you didn't know, the laptop has a "Hybrid Graphics System" such that you can switch between an Intel GMA 950 and a Nvidia 7400 Go. I used [this page]("http://ariel.vardi.free.fr/ariel//vaiosz.html") to set up a script for switching xorg.conf when required. I then proceeded to get GLX/Beryl working on the Nvidia card. My problem is that I cannot seem to enable GLX on the Intel card. I believe this has something to with the glx module being for nvidia and not working on Intel. Can someone please help me? I would like to have a script that switches these modules and all other requirements on bootup, but I would have no idea how to go about that or what to change. I found [this page]("http://www.sabi.co.uk/Notes/linuxNVIDIA.html") but I don't know how to automate that, or even if it applies to Ubuntu. Thanks.

In xorg log:
...
LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
...
Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
...

BTW my xorg.conf has all required stuff (Load glx, etc.).

---

### Post by Khan of Khronos on 2007-04-26
*bump*
Does anyone know?!

---

### Post by Khan of Khronos on 2007-05-02
Should this go somewhere else?

---

### Post by cem on 2007-05-07
sudo gedit /etc/init.d/xorg_conf and paste the text below

```
VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf.speed /etc/X11/xorg.conf
modprobe drm
modprobe nvidia-agp
rm /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/libGL.so.1 -f
ln -s /usr/lib/xorg/modules/libglx.so.1.0.9631.bak /usr/lib/xorg/modules/libglx.so
ln -s /usr/lib/libGL.so.1.0.9631.bak /usr/lib/libGL.so.1
else
modprobe intel-agp
cp -f /etc/X11/xorg.conf.stamina /etc/X11/xorg.conf
rm /usr/lib/xorg/modules/libglx.so /usr/lib/libGL.so.1 -f
ln -s /usr/lib/xorg/modules/extensions/libglx.so.bak /usr/lib/xorg/modules/extensions/libglx.so
ln -s /usr/lib/libGL.so.1.2.bak /usr/lib/libGL.so.1
fi
```

you may have to uninstall nvidia-glx and reinstall libgl1-mesa-glx to enable backup of libGL.so.1.2 and libglx.so, then reinstall nvidia-glx (synaptic) and create backup of ibGL.so.1.0.9631 & ibglx.so.1.0.9631
Finally sudo ln -s /etc/init.d/xorg_conf /etc/rc2.d/S12xorg_conf.

---

### Post by Baggsy on 2007-11-04
Bumping this as I also have a Vaio SZ-series I want to use.

Can someone please explain how to do this for an absolute noob? I tried creating the script, but got told I don't have the permissions for it, however I have no clue how to get root when I'm in the GUI, and doubly so no clue on how to do it in the terminal.

Tried googling around a bit and also searching the forums, but got rather confused.


Thanks.

---

### Post by Baggsy on 2007-11-04
Sorry for the double post.

I managed to get the script and the two different xorg.conf files placed by running gedit with sudo from terminal.

However, I'm trying to figure out how to soft link the script into rc2.d so the position of the switch will determina startup.

Lastly, I installed Gutsy when the Intel chipset was active, and when I try booting with the nVidia chip I only get a command promt. Can anyone tell me what I need to do to install the nVidia driver and start the desktop from there?

---

### Post by bazzard on 2007-11-04
I'd like a solution to getting the speed/stamina switch working fully too for a n00b also! Cheers

---

