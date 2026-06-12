---
title: "nvidia graphics driver help"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by p3ngu1n on 2007-07-18
ok, so, i got a driver off of nvidias homepage for nvidia geforce 6200 AGP on linux x86 (i dont realy know what my system is but x86 always works) and every time i boot i get a black-screen login were it tells me that x doesnt work. i got it to work by reinstalling and then typing startx. i know have to do that EVERY TIME. when i read the error report, it says something like: "driver is 100.14.11 but kernel doesnt match". please help me!
.

---

### Post by Hobo Joe on 2007-07-18
```

sudo dpkg-reconfigure xserver-xorg

```

Leave everything at default except the graphics driver option, select vesa on that.

Then get Envy.(I have a link on my sig.) Install and run, then select 'install nvidia driver'. Make sure to let it configure xorg for you.

---

### Post by Kobalt on 2007-07-18
Or if you want to install it manually you should [read this]("http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2").
Though I strongly advise, if you're not an Ubuntu skilled user, to use the nVidia drivers from the repositories.

---

### Post by Medieval_Creations on 2007-07-18
I have a GeForce 6200 and using the nVidia driver in the repositories worked fine for me.

You just need to install it and reconfigure xserver.

Install:
sudo apt-get install nvidia-glx

Reconfigure (Same as Above):
sudo dpkg-reconfigure xserver-xorg

---

