---
title: "How do I know if I have ati drivers installed?"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-12-01
Hello. I actually have been using ubuntu for some months now, but I have not used any graphics hungry programs. I want to try using some of these programs now, so I would like to know how I know If I have installed any proper drivers for this purpose.

---

### Post by madmetal on 2006-12-01
just open terminal and type
 glxinfo | grep direct 
if the answer is yes then you have 3D acceleration on!

---

### Post by jincast90 on 2006-12-01
Ok this is what I get when I type  glxinfo | grep direct :

libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes


What does this mean?

---

### Post by madmetal on 2006-12-01
i dont know what it means but i found this one..
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/58541](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/58541)

---

### Post by jincast90 on 2006-12-02
bump..

---

### Post by lamego on 2006-12-02
1) They are only installed if you have installed them, ATI drivers are not installed with the system install.
If you need them installed a good way to check it would be to just request them to be installed with:
```
sudo apt-get install xorg-driver-fglrx
```
2) Being installed does not mean it is being used

If you need full instructions on how to install/configure the ATI driver read:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

