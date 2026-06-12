---
title: "Better refresh rate with nvidia"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by ex_win_slave on 2007-06-28
I have just installed nvidia drivers to my computer with Alberto Milones Envy(Excellent!!) so how i can get better refresh rate??? I want use 1280x1024 but there is on 50hz refresh rate,i want use 1280x1024@75hz rate(old monitor) how?:guitar:

---

### Post by FuturePilot on 2007-06-28
Open the Nvidia Settings tool. Applications>System Tools and go to the Xserver Display Configuration. There will be on option to set the refresh rate. It should list the correct ones. But you'll have to do that every time you reboot so you'll have to save the settings to your xorg.conf file. You need to run Nvidia settings as root in order to do this.
```
gksudo nvidia-settings
```

But be warned, when you do that it might also remove some stuff from your xorg.conf file. Best to make a back up first.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```
When I did that on my laptop it removed the whole section for the touchpad and it no longer worked. I had to add all that back in from the back up file.

---

### Post by ex_win_slave on 2007-06-28
First:i m sorry because i forget say:my ubuntu version is 6.06LTS and my graphcard is nividia geforce 6200 with 256mb memory.but i cant get resolution 1280x1024@75hz. so what i have try to do next?? :guitar:

---

