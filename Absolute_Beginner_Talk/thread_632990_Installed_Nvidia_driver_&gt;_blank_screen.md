---
title: "Installed Nvidia driver &gt; blank screen"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by halohunter on 2007-12-06
I just installed a new copy of Gutsy on my laptop. Following recommendations I installed the nvidia restricted driver and restarted the computer. Now all I get when I boot is a black screen.

It seems as if it is working, I can log in and do everything blindly. However the screen is black.

Ctrl-Alt-F1 opens the command prompt.

Help please!

---

### Post by PmDematagoda on 2007-12-06
Do:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
in a terminal.

After that do:-

```
sudo startx
```

And could you post what VGA card you are having?

---

### Post by halohunter on 2007-12-06
I have a Geforce4 420 Go

After doing the above I get:

> fatal server error. Server is already running for display 0
connection to 0:0 refused by server
invalid MIT-MAGIC-COOKIE key
giving up
unable to connect to x server
no such process server error
error in locking authority file /home/hassan/.Xauthority

---

### Post by PmDematagoda on 2007-12-06
Do:-

```
sudo /etc/init.d/gdm stop
```

And then do the commands I posted before.

---

### Post by halohunter on 2007-12-06
ok, thanks that got me into the desktop. What should I do now to get the nvidia card working?

---

### Post by kpkeerthi on 2007-12-06
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver)

This is the recommended method to install nvidia driver.

---

