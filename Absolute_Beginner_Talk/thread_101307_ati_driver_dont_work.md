---
title: "ati driver dont work"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by Mazoku on 2005-12-09
Hello.
I'm new in linux so i ask here, I'm try install ati driver on my ubuntu system ( 5.10 ) i read [BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29")
but it's not help me.

```
mazoku@maou: ~$ lspci
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5e4b
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5e6b

``````

mazoku@maou:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

``````

(II) Module vbe: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

Fatal server error:
Module load failure

```
My configuration:
M/B: Asus a8n-e nforce4
CPU: AMD64 3000+
Video: PCI-E ati x700pro

---

### Post by Rackerz on 2005-12-09
ATI has never really cared about the Linux users. I don't think the ATI drivers are needed. There already installed by default i think.

---

### Post by Mazoku on 2005-12-09
> ATI has never really cared about the Linux users. I don't think the ATI drivers are needed. There already installed by default i think.
Default driver don`t work too. 

The problem is solved, read 
[here]("http://ubuntuforums.org/showthread.php?t=75378")

---

