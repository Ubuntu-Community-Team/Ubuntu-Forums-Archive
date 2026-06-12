---
title: "[SOLVED] nvidia drivers not activating, wine wow, werd permissions"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2006-11-01
Hello, total newbi here so please be very detaled with help.
was installing wine to run wow and get away from windows when i was like i still need to install drivers for my nvidia geforce 7900 gtx 
so started to do that by useing this guid [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
were i got hung up was in the install and activate drivers part on the 10 step
ran code 
sudo nvidia-glx-config enable 
and got back 
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
dont know what this means exactly 
so then i did the Ctrl-Alt-Backspace thing and no logo so it didnt work
ran agin and try to see if i could edit that file
found file couldn't save any changes not that my changes would have helpe.
all help would be aprecated.

---

### Post by tseliot on 2006-11-01
Try this:
```
sudo nvidia-xconfig --no-composite
```

then restart the Xserver:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use kdm)
```

---

### Post by blendmaster on 2006-11-01
Wait, so you can't get into a GUI (your desktop)?

If not, boot into recovery mode, and use sudo nano /etc/X11/xorg.conf,find the section labeled "drivers", and change the word "nvidia" to "nv".

After that, press ctrl-x, y, then enter. Restart the computer, and I think you should be good.

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-11-01
yay figured it out thanks guys!

---

