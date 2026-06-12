---
title: "nvida graphic card"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Pinon on 2007-02-07
I can't see how to install the correct driver for the graphic card on my computer.

The graphic card is a NVIDA GeForce Go 7300, and the computer uses an Intel Core Duo processor T2050, and the linux ubuntu version is Edgy Fit,v. 6.10.

Do any have an idea?


Thank you.

---

### Post by flossgeek on 2007-02-07
Ensure your repostorys are enabled, you will need multiverse:-

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)

Once your repos have been added install the nvidia package:-

```
sudo apt-get install nvidia-glx
```

Then issue:

```
sudo nvidia-xconfig
```

For more details see:- [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

** Note when I installed the Nvidia driver, I didnt issue nvidia-xconfig, i just opened **/etc/X11/xorg.conf** and changed the driver name from "nv" to "nvidia".*

You can open xorg.conf with following command:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by milad on 2007-02-07
try automatix, I have 7300 GT and the driver was installed in a sec, no command or configuration needed.

---

