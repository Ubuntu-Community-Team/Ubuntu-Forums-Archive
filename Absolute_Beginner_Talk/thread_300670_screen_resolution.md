---
title: "screen resolution"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by imgadget on 2006-11-16
i've just loaded ubuntu 6.1 and i would like to have a higher screen resolution than 1024x768 and i definitely need a better refresh than 60hz. i have an nvidia 7800 and i downloaded the latest drivers (nvidia-linux-etc...) from the nvidia site. i changed the file to an executable but when i try to run it from the desktop nothing happens and when i try to run it in the terminal it says i need to 'exit x' to run it. the nvidia site says i need to change the runlevel how do i do this? or can i change all my display settings without it?
any help is greatly appreciated
thanks
g

---

### Post by Bachstelze on 2006-11-16
Hi and welcome to Ubuntu :)

To install the drivers from the official nvidia installer, you need two things, the headers for your running kernel and the gcc, to install them, run this :

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

When all of it is installed, switch to a console with Ctrl+Alt+F[1~7], become root with

```
sudo -i
```

stop your X server with

```
/etc/init.d/gdm stop
```

and then run the installer with

```
sh /path/to/package.run
```

And finally start your X server again

```
gdm
```

Voilà :)

A low-hassle way to do this is to use the Ubuntu packages for the drivers instead. To install them, do this

```

sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx
sudo nvidia-glx-config enable
```

and then restart your X server with Ctrl+Alt+Backspace.

---

### Post by CatKiller on 2006-11-16
[nVidia binary driver how-to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

