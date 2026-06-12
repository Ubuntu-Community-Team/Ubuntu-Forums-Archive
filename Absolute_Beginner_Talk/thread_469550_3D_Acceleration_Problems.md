---
title: "3D Acceleration Problems"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by kimcheefreak17 on 2007-06-10
Hi I've just finished installing my graphics driver for an ATI Radeon 9600. I then went to verify if I had correctly installed the driver by putting:

 ```
fglrxinfo
```
 in the terminal. This didn't return what the guide said it should, but rather, it returned with:
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

I went into the trouble shooting section and did what I was told,
```
mkdir -p /usr/X11R6/lib/modules/dri 
ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 
```

Which didn't change anything. Then it advised me to:

```
lsmod | grep fglrx
```

Which returned:
```
fglrx                 540004  0 
agpgart                35400  2 fglrx,intel_agp
```

The next steps were only if the above command didn't give an output, but it did. So I'm stuck in a little pickle here. It'd be great if anyone could help out with my problem.

---

### Post by dannystaple on 2007-06-10
HI there,
There are plenty of guides, so could you possibly point me at which you were looking at?
For now I will assume [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).
Also which system (version of Ubuntu) are you using?

Part of this guide suggests that if the Feisty setup deos not just work, to start following the Edgy part, including making entries in the xorg.conf file. Did you follow this part of the guide?

Cheers,
Danny

---

### Post by kimcheefreak17 on 2007-06-10
Right now I'm using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

And I'm running Feisty. I'll try using the guide you directed me to. Thanks!

---

