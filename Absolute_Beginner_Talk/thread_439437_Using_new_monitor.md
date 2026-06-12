---
title: "Using new monitor"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Bluecube on 2007-05-10
My current monitor is a 1280x1024 job. If I plug in a widescreen 1680x1050 monitor will Ubuntu autodetect the new monitor and change resolution as required? If not what do I need to do to make the process as smooth as possible?

---

### Post by taurus on 2007-05-10
You probably need to boot into recovery mode from GRUB menu and reconfigure X, especially the monitor section, for your machine again.

```
dpkg-reconfigure -phigh xserver-xorg
```
Or you can add that resolution in /etc/X11/xorg.conf if you wish.

```
nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by annda on 2007-05-10
EDIT: taurus was faster - as always :-)

no, ubuntu will not automatically change anything. it will detect the monitor just fine, but the user is responsible for making changes to the system.

how hard that will be depends on your video card drivers. the current resolution is safe, so the new monitor will be usable with that.

if you have nvidia, you can use its settings tool to change the configuration.

you can also always run this from the terminal (after plugging in the new monitor):

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

