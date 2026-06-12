---
title: "nvidia-kernal.........."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-17
i deleted my nvidia-kernel cuz it said to do that on the linux nvidia forum....i was trying to install the nvidia driver. after i deleted that it said to close x server. so i did that and forgot couldnt figure out how to get that driver i downloaded. so i restarted and now it cant read  my monitor or something (theres that one box that floats around the screen when you turn on your monitor but its not plugged in). im using my boot disk right now. is there a way to reinstall nvidia-kernel to the init.d director from the boot disk?

---

### Post by PmDematagoda on 2008-04-17
I am not sure about reinstalling the nvidia-kernel, but you can boot Ubuntu in Recovery Mode and execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to reset the X-Server configuration, after reconfiguration you can restart with:-
```
sudo reboot
```

---

