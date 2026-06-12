---
title: "Anyone with an  Nvidia MX4000 able to use glx 9755 driver ?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by linuxnooby on 2007-05-19
I am wondering if it is possible to use the glx 9755 package with MX 4000 card. Have removed the glx 9631 packages and installed the 9755, only to lose xwindows and have to go through the DPKG_-reconfigure xserver-xorg routine and then reinstall the 9631 package.

Any advice would be appreciated.

---

### Post by xpod on 2007-05-19
Any particular reason why you dont want to use the 9631 driver if it works?
I have the mx4000 and the 9631 drivers work great including beryl etc.

---

### Post by Bachstelze on 2007-05-19
The 97xx drivers do not support this card. You'll have to stick with the 96xx.

---

### Post by linuxnooby on 2007-05-19
Thanks for the replies. I just thought that a newer driver might produce better results. As a matter of interest, what results do you get when running glxgears ?

Whilst on the subject, having messed around in synaptic, removing/reinstalling video driver packages, I can not now use the 9631 drivers. Any ideas as to which packages should be removed from Synaptic and which must be installed ?

---

### Post by Bachstelze on 2007-05-19
Which Ubuntu release are you running ?

---

### Post by linuxnooby on 2007-05-19
7.04

---

### Post by Bachstelze on 2007-05-19
Then just remove nvidia-glx-new and install nvidia-glx instead.

---

### Post by linuxnooby on 2007-05-19
Thanks, but is there a difinitive list of items which must/must not be installed for the glx to work ? I ask this because I have been removing various items and installing others, which may conflict

---

### Post by Bachstelze on 2007-05-19
Not that I know of. Just install nvidia-glx and the restricted moduls for your current kernel and you will be fine.

---

### Post by linuxnooby on 2007-05-20
In the end I had to uninstall/reinstall via Envy.

Got my 3D graphics back, now

---

