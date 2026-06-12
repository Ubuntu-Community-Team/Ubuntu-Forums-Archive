---
title: "Can't use max screen resolution..."
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Scotch on 2006-11-17
Hello. 
I've just installed nVidia drivers for Edgy. And followed the step-by-step guide located here: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)


I believe the drivers should be properly installed. But when I go to System -> Administration -> Screen resolution I'm not allowed to set it above 1024 width. My screen supports 1280.

Some help please?
Thank you.

---

### Post by taurus on 2006-11-17
You probably need to add that, 1280, to /etc/X11/xorg.conf.

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by srehpog on 2006-11-17
Can you go to Applications -> System Tools -> NVIDIA X Server Settings and change it there to 1280x1024?

---

### Post by shanepardue on 2006-11-17
I've had SOO many problems with resolutions and refresh rates on Edgy. That 
was the reason i went back to Dapper. Edgy had some cool stuff, but it wasn't 
worth the headache. Hopefully Feisty Fawn will work better with that stuff.

---

### Post by srehpog on 2006-11-17
I had the problem too, but once I installed the new NVIDIA drivers I just set it in the NVIDIA X Server Settings and then wrote it to my xorg.conf file by a click of a button.

---

### Post by shanepardue on 2006-11-17
Yeah, if the Nvidia settings don't write to the xorg.conf when you click it, 
(mine didn't) you can view what it would write and just copy and paste it 
into your xorg.conf. Also, you can search modelines in the forums for one 
other tactic of forcing resolutions and refresh rates. I did all of this and 
nothing worked for me, but I hope it does for you!

---

### Post by srehpog on 2006-11-17
In terminal:
sudo nvidia-settings

Then the program can write to the file.

---

### Post by Scotch on 2006-11-17
> **taurus said:**
> You probably need to add that, 1280, to /etc/X11/xorg.conf.

```
gksudo gedit /etc/X11/xorg.conf
```

Thank you:D  Worked great:mrgreen:

---

### Post by shanepardue on 2006-11-17
AWESOME! that's good news!

---

