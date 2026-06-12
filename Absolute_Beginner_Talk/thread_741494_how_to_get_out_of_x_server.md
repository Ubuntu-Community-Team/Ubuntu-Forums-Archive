---
title: "how to get out of x server"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by overdrank on 2008-03-31
> **Auston said:**
> recently i ve downloaded nvidia driver for fedora 8....which in order 2 install requires stopping the x server..........i have entered into the console by pressing "alt+f3" but it didnt help...........
what shud i do...am i suppose to run the fedora in run level : single user by making changes into the xorg file ...it seems quite dangerous 2 me as i am new 2 linux.....it might not switch back 2 run level 5.............what shud i do ...please help

Hi and you can try ```
sudo /etc/init.d/gdm stop
``` as I have not used Fedora 8 much
[http://webwork.maa.org/wiki/Installation_Manual_for_2.3_on_Fedora_Core_7?rev=1.3](http://webwork.maa.org/wiki/Installation_Manual_for_2.3_on_Fedora_Core_7?rev=1.3)
:oops::-$

---

### Post by warp99 on 2008-03-31
In Ubuntu you would press crtl-alt-f2, login to the console then type:

```
sudo killall kdm
```

if you have KDE or:

```
sudo killall gdm
```

if you have Gnome. Install your drivers according to the Nvidia guide and reboot since the new kernel modules need to load. Hope this helps.

---

