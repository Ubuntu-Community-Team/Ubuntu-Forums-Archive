---
title: "Glx"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by ezze66 on 2007-11-04
can someone help with my video ?

eze@eze-desktop:~/Desktop$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


my video chipset is via unichrome P4M900
i want to install video drivers so i can have better refresh rates

thanks

---

### Post by ezze66 on 2007-11-04
bump...

---

### Post by carlinuxlearner on 2007-11-04
Open up a terminal window and type in this "lspci | grep VGA" post output here (to open a terminal Applications>>Accessories>>Terminal).

C@RL

---

### Post by Maestro23 on 2007-11-04
This thread might help: [http://ubuntuforums.org/showthread.php?t=485646&highlight=Unichrome](http://ubuntuforums.org/showthread.php?t=485646&highlight=Unichrome)

---

### Post by ezze66 on 2007-11-04
eze@eze-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3371 (rev 01)

---

### Post by overdrank on 2007-11-04
> **ezze66 said:**
> eze@eze-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3371 (rev 01)

Hi if you will run this command in the terminal ```
sudo update-pciids
``` this will update your ids and identify. Also for screen resolution this link may help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by ezze66 on 2007-11-04
ok 
_ now the **lspci** | grep VGA shows this:_

[B]eze@eze-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)

[/B]_and also the **glxinfo** changed:_[B]

eze@eze-desktop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

[/B]

---

### Post by ezze66 on 2007-11-05
bump

---

### Post by erginemr on 2007-11-05
I cannot help you first hand, because I am using NVIDIA Geforce 4 MX as the graphics card, it seems that your VIA Chrome9 card is not suported well under Linux. I have managed to find 3 sites that propose steps to install the correct driver. Maybe you can make something out of it:

[https://answers.launchpad.net/ubuntu/+question/11807](https://answers.launchpad.net/ubuntu/+question/11807)
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

Good luck...

---

### Post by ezze66 on 2007-11-05
ok thanks! i will give those sites a look.

another problem, 
everytime i change my xorg.conf configuration from "vesa" to "via", when i restart X server will not load. i tried "openchrome" but display was messed up.

any help.

---

### Post by ezze66 on 2007-11-05
anyone?

---

### Post by erginemr on 2007-11-05
> **ezze66 said:**
> ok thanks! i will give those sites a look.

another problem, 
everytime i change my xorg.conf configuration from "vesa" to "via", when i restart X server will not load. i tried "openchrome" but display was messed up.

any help.

Sorry, I wish I could help. But it should not be that simple as changing names of the drivers. You may consider checking whether the following packages have been installed from synaptic:
xserver-xorg-video-via
xserver-xorg-video-unichrome
xserver-xorg-video-openchrome

Maybe, after installing those, you will be able to use "via" or "openchrome".

---

