---
title: "nvidia-glx driver problem"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-06-28
i have a nvidia gf 6600 gt agp 8x (128 mb 500/900)
i've just installed the nvidia-glx driver. i enabled it by ```
sudo enable nvidia-glx-driver-config
```  or something like this. It said I have to restart the X server. I restarted my pc and now it says: ```
Failed to start the X Server (your graphical interface). It is likely that it is not set up 
correctly. Would you like to view the x Server Outpot to diagnose the pb? YES/NO
``` I chose yes and now at warnings it says ```
(WW)NVIDIA: no mathing device section for instance (BusID PCI:2:0:0) found
``` and at errors ```
(EE)No devices detected
```

---

### Post by FredB on 2006-06-28
Erh... Looks like you xorg.conf file is rotten is some ways.

Can you paste the content and post it here using sudo gedit /etc/X11/xorg.conf

I got this with my "old" GeForce FX5200 :

```

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

```

Maybe the answer is here ?

---

### Post by FuzZy2006 on 2006-06-28
well, i've got a nvidia gf 6600 gt and the code is definitely for a fg 5200 :(. how can i reinstall xserver to make it work as before? cos' i heard that to remove it i have to use command ```
apt-get remove xserver-xorg
```   Pls heeelp.

---

### Post by richbarna on 2006-06-28
[QUOTE=FuzZy2006]well, i've got a nvidia gf 6600 gt and the code is definitely for a fg 5200 :(. how can i reinstall xserver to make it work as before? cos' i heard that to remove it i have to use command ```
apt-get remove xserver-xorg
```   Pls heeelp.[/QUOTE]

when you log on, type this >/

> sudo dpkg-reconfigure xserver-xorg

and just follow the instructions.

Did you follow this guide ? :-

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by FuzZy2006 on 2006-06-28
thx, it worked

---

### Post by FredB on 2006-06-28
[QUOTE=FuzZy2006]well, i've got a nvidia gf 6600 gt and the code is definitely for a fg 5200 :(. how can i reinstall xserver to make it work as before? cos' i heard that to remove it i have to use command ```
apt-get remove xserver-xorg
```   Pls heeelp.[/QUOTE]

I know. But both cards install the same way.

The important line is one with driver in it !

---

