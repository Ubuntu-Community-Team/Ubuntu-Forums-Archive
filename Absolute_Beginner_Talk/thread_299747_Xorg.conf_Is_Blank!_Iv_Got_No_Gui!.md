---
title: "Xorg.conf Is Blank! Iv Got No Gui!"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Sheepish on 2006-11-14
Please help me, i have been following HOWTOs on changing graphics drivers to the nvidia ones, iv changed from ATI to NVIDIA, and when i installed the driver using ENVY everything was fine, untill i rebooted, then it tells me that xserver fails to start and iv got no gui! im stuck in terminal.i have also been told to edit XORG.CONF but i come to find its empty, i believe this is bad. Please help

---

### Post by taurus on 2006-11-14
It is /etc/X11/xorg.conf!  Remember, Linux/Unix is case sensitive...  Otherwise, you can configure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bodhi.zazen on 2006-11-14
:lol:

DON"T PANIC -  TOO LATE ! :p

how did you open xorg.conf? nano or vi ?

Assuming nano, try:```
sudo nano /etc/X11/xorg.conf
```

Also you should have a back up, no ? (ls /etc/X11)

If not, open a terminal and type:> I will back up system files before I alter them100 times !! :p

Did we forget how to ```
dpkg-reconfigure -phigh xserver-xorg
``` ???

You also forgot to tell us:
[indent]Video card
What method were you using to install the nvidia drivers[/indent]

---

