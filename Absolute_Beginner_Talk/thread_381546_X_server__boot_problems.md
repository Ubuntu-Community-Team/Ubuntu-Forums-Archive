---
title: "X server / boot problems"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Frickalik on 2007-03-11
Hello. I am semi-new to Linux . I have installed on a bunch of older systems and now i tryed to put Ubuntu on my main-comp on a seperate harddrive.  With the 6.10 boot cd i get a x server error. so i used the alternate cd to install.  i get everything installed and go into recovery mode (press esc during "gnome loading") i enter as "root". I install all of my nvidia drivers ( nvidia-glx install nvidia-kernel-common, my 8800 Driver, and a bunch of other b.s. to make my driver install i.e. apt-get install "make" "gcc") 

So i restart and i get a X server error. saying that NVIDIA is no detected. SO i opened my xconf and changed my driver from NVIDIA to nv. Which fixed that error.

I still cannot figure out how to fix the following error.

(==)using config file:"/etc/X11/xorg.conf"
(ee) Failed to load module "glx" (module does not exist, 0)
(ee) No devices detected.

Fatal server error:
No screens found

I dont want any b.s. on its my hardrive or my video card is too new. If anyone knows how to fix the flx the glx error. I think it might a conflict between the nvidia-kernel and the nvidia-glx...someththing about merged. But lk i said, im new to linux so if anyone is going to go that route please go step by step.

Thank you

---

### Post by Frickalik on 2007-03-11
The comp is :

Intel e6600
8800gts 640
80 gb western dig Sata
Asus p5w-dh mobo

---

### Post by STREETURCHINE on 2007-03-11
can you post the out put of 

    ```
cat /etc/X11/xorg.conf
```

---

