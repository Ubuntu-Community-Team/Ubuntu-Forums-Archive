---
title: "nVidia Drivers problem"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by meanburrito920 on 2007-06-27
I am trying to enable 3D support for my nVidia FX 5200 card. When I selected the option, it told me that I needed to install new drivers through Synaptic. I installed the drivers that claimed to be for cards above model # 3200. However, when I rebooted the X server, it crashed and said that the drivers were not working. I used the terminal to revert the old drivers, but this means I don't have 3D support. Did I install the wrong drivers? What was the problem? thanks for any help in advance.

---

### Post by cogadh on 2007-06-27
Use these instructions to properly install the driver:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)
I also have a FX 5200 and it works great using the nvidia-glx-new drivers.

---

### Post by meanburrito920 on 2007-06-27
Sorry, I forgot to mention I'm running Edgy...

---

### Post by cogadh on 2007-06-27
In that case, use this one:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Oh, and you should use Method 1 on that instruction. Method 3 will lead to problems later on if you ever update your kernel.

---

### Post by meanburrito920 on 2007-06-27
The driver installed fine, but now a bunch of stuff isnt working, such as Blender3D and some of the screensavers. Why?

---

### Post by cogadh on 2007-06-27
Check your /etc/X11/xorg.conf file's Device section. It should look something like this:
```
Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection
```
If the Driver entry says "nv" and not "nvidia" as above, then the accellerated driver is not active. Modify the entry, save the file, log out, then hit CTRL-ALT-BKSPC to restart the X server.

---

### Post by meanburrito920 on 2007-06-27
I dont have permissions to edit the file, but it was showing "nv"

---

### Post by cogadh on 2007-06-27
Open a terminal and run this to backup you xorg.conf:
```
sudo cp /etx/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then run this to edit it:
```
sudo gedit /etc/X11/xorg.conf
```
If you are using Kubuntu, then do this instead:
```
sudo kate /etc/X11/xorg.conf
```
It will ask for your password, then you will be able to edit the file.

When you restart X, if it fails to launch, do this:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by meanburrito920 on 2007-06-27
thanks for the help, it all worked except for the fact that the screen now pops up about 10 pixels to the left and I have to do a factory reset on my monitor to get it fixed (if I try and edit my monitors settings manually, it jumps to about 30 pixels off and wont go back). Is there a way to fix this? I had the same problem when I have booted from the liveCD

---

### Post by cogadh on 2007-06-27
It just needs to have the correct horizontal sync and vertical refresh rates entered in the xorg.conf file. If you don't know that info, let me know what manufacturer/model it is, I can figure it out.

---

### Post by meanburrito920 on 2007-06-27
It's a Dell, but I have no idea where to find the model #.

---

### Post by meanburrito920 on 2007-06-27
Actually, I just rebooted and it seems to be working now. Weird... anyway, thanks for your help.

---

### Post by cogadh on 2007-06-27
You're welcome, glad to help.:)

---

