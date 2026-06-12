---
title: "How Do I Install nVidia glx?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by elangley on 2007-04-24
I just installed ubuntu on my homemade pc for the first time and my wireless card doesn't work nor does my nvidia graphics card, can anyone help me on how to install drivers for them to work? i can burn cd's if i need to (i'm on a macbook pro trying to figure out how to fix it.)

---

### Post by phidia on 2007-04-24
It would help to know the specs of that hardware. 
If the nvidia gpu is fairly recent you can install nvidia-glx-new with your preferred package manager.

---

### Post by 5-HT on 2007-04-24
1. Video Drivers
If you're running Feisty: Simple as System > Administration > Restricted Drivers Manager and check 'Enabled'. 
If you're running any other version of Ubuntu: 
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```2. About the wireless drivers, please post what card you have so somebody can start to help.

Hope that helps.

---

### Post by elangley on 2007-04-24
it's an nvidia geforce fx 5800

---

### Post by elangley on 2007-04-24
and the wireless card is a dynex wireless g card

---

### Post by elangley on 2007-04-24
also, i clicked enabl in the restricted drivers, but it didn't enable, a window popped up that said:enable the driver? and i click enalbe driver and nothing happens

---

### Post by banditv1 on 2007-04-24
When you enabled the drivers for the video card, did you reboot the gui or computer ?

---

### Post by elangley on 2007-04-24
i went to the top right corner of the screen and clicked on restart, so i restarted the entire system.

---

### Post by elangley on 2007-04-24
i also downloaded the nvidia-glx.deb package on my mac and burned it to a cd, but when i click on the package in ubuntu is gives me this error: Depenency is not satisfiable: nvidia-kernel-1.0.8776

---

### Post by banditv1 on 2007-04-24
This post has some good information that may prove useful.

[http://ubuntuforums.org/showthread.php?t=419546](http://ubuntuforums.org/showthread.php?t=419546)

---

