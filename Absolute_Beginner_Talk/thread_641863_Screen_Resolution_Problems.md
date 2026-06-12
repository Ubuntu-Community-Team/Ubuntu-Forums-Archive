---
title: "Screen Resolution Problems"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Want A Pie on 2007-12-15
Hi, in my long journey to get my sound working on Ubuntu (which still isn't working), I have made my screen resolution go very very bad. Everything is larger, and I can't change the resolution from 640X480 in the Screen Resolution Prefrences. 
I hope someone can help, as I have only had Ubuntu for a few days, and I haven't managed to look around it because I have been trying to fix problem after problem. This is the first problem I've had that didn't come with the OS, so I hope someone can help.

Thanks in advance

EDIT: After doing Taurus' suggested code, the resolution is fine for the login screen, but when it logs in, the resolution goes back to its dodgyness :(

---

### Post by taurus on 2007-12-15
What graphic card do you have and have you installed a driver for it?  If you need to reconfigure your X server, open a terminal and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, either restart X with <Ctrl><Alt>Backspace or reboot.

---

### Post by Want A Pie on 2007-12-15
I did it, but it didn't work
the login screen, however, was back to normal, but everything else isn't (I wish it was the other way)

---

### Post by taurus on 2007-12-15
To tell the X server to read in the new config, /etc/X11/xorg.conf, that you have just created/modified.

---

### Post by Want A Pie on 2007-12-15
> To tell the X server to read in the new config, /etc/X11/xorg.conf, that you have just created/modified. 

OK... I have no idea what that means

---

### Post by skyjacker on 2007-12-15
Try this Procedure:

1) Back up the present xorg.conf
Code :sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

2) Stop gdm or kdm
Code: sudo /etc/init.d/gdm stop (or kdm for kde)

3) Edit xorg.conf
Code: sudo dpkg-reconfigure xserver-xorg

4) Select the resolutions you want available by arrowing down to each desired line and pressing the ?space bar?

5) Validate your choices with ?enter?

6) restart X with Control+Alt+Backspace

7) Choose the desired resolution under the ?Systems/Preferences/Screen Resolutions drop down list

NOTE: if you don't need to add any additional resolution sizes, skip # 4 & 5

---

### Post by tekwerx on 2007-12-16
If his login screen is working correctly, it could be that he needs to do something as simple as going to System, Preferences, then Screen Resolution and choosing something different there.

---

### Post by Want A Pie on 2007-12-16
got it working :D
thanks, btw taurus' code did work :P

---

### Post by tekwerx on 2007-12-16
> **Want A Pie said:**
> got it working :D
thanks, btw taurus' code did work :P

Great!  :)

---

