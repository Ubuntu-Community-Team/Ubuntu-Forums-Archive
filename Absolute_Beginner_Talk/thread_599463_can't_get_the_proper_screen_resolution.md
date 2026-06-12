---
title: "can't get the proper screen resolution"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-01
I can't get the proper screen resolution anymore.  After I install my drivers it won't detect that my screen resoluton is 1440x900.  Can anyone help me

---

### Post by taurus on 2007-11-01
What graphic card do you have and how did you install that driver?

---

### Post by Inxsible on 2007-11-01
1) ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
2) ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
3) Select all the resolutions that you want using the space bar.


Note: You will have to re-enable your graphics drivers, if you are using the restricted ones. You will also have to reconfigure dual monitors etc. if you are using any.

---

### Post by Dapman01 on 2007-11-01
I am currently using a 6200 LE and am using nvidia drivers

---

### Post by Dapman01 on 2007-11-01
> **Inxsible said:**
> 1) ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
2) ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
3) Select all the resolutions that you want using the space bar.


Note: You will have to re-enable your graphics drivers, if you are using the restricted ones. You will also have to reconfigure dual monitors etc. if you are using any.

patrick@patrick-desktop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
patrick@patrick-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071101102019
patrick@patrick-desktop:~$ 

that is what I got, nothing else

---

### Post by skyjacker on 2007-11-01
Try this Procedure:

1) Back up the present xorg.conf
Code :sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

2) Stop gdm or kdm
Code: sudo /etc/init.d/gdm stop (or kdm for kde)

3) Edit xorg.conf
Code: sudo dpkg-reconfigure xserver-xorg

4) Select the resolutions you want available by arrowing down to each desired line and pressing the “space bar”

5) Validate your choices with “enter”

6) restart X with Control+Alt+Backspace

7) Choose the desired resolution under the “Systems/Preferences/Screen Resolutions drop down list

NOTE: if you don't need to add any additional resolution sizes, skip # 4 & 5

---

### Post by alienexplorers on 2007-11-01
Have you tried using nvidia-settings.  Run it from terminal like this:
> gksudo nvidia-settings

---

### Post by Dapman01 on 2007-11-01
worked out great thanks.  
quick question, how do you get coolbits to work through the synoptic package

---

### Post by alienexplorers on 2007-11-01
> Option "Coolbits" "integer"
I believe 1 enables it and 0 disables it.

---

