---
title: "Xgl error"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by g1psas on 2007-03-22
I tried to install xgl and after restart - the error: (OS - ubuntu 6.10)
"GDM: xserver not font :/ust/xgl :0 :0 -fullscreen - ac -accel glx: pbuffer - accel xv: fbo - auth /var/bib/gdm/ :0.Xauth - nolisten tcp vtt
Error: commend could not be executed. Please install the x server or correct GDM configuration and restart GDM. "
Can anyone help my? I am beginner in linux

---

### Post by mrmonday on 2007-03-22
If you hit enter/press arrow keys can you get to a prompt? If you can try:

```
dpkg-reconfigure xserver-xorg
```

Just follow the instructions, and got with the defaults. What now?

---

### Post by g1psas on 2007-03-22
"package 'xserver-org' is not installed and no info is available.
....
usr/sbin/dpkg-reconfigure: xserver-org is not installed. "

---

### Post by g1psas on 2007-03-22
P.S. installing xgl i followed this guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29)

---

### Post by mrmonday on 2007-03-22
This is a problem...

Did you do this step?

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

If so do:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
Reboot.
What happens now?

---

### Post by g1psas on 2007-03-22
Maybe I did that, because I followed the instruction step by step, but there is no such file :(

---

### Post by mrmonday on 2007-03-22
Try:

```
sudo apt-get install --reinstall xserver-xorg
```

---

### Post by g1psas on 2007-03-22
apt-get COMMAND  not found :(

---

### Post by mrmonday on 2007-03-22
Do you have any important files on there? It looks like your best option might be a re-install. If you have important files, say so and we will talk you through it

---

### Post by g1psas on 2007-03-22
No I haven't. I installed ubuntu only yesterday and I wanted something more - like xgl :)  I think i will reinstall ubuntu tommorow. Thanks for trying to help me :)

---

### Post by mrmonday on 2007-03-22
Sorry I couldn't help more :( - I am pretty much a linux newbie myself...

I recommend beryl... I know it's beta, but it works nicely and most of the bugs have been worked out :)

---

