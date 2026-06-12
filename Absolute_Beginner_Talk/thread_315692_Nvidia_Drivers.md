---
title: "Nvidia Drivers"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by zeroooooooooooo on 2006-12-09
In Dapper, I am trying to install the drivers for my EVGA Geforce 7600GT video card, and I am running into issues.

Following the instructions here ([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)) I get to the point where I am in the terminal typing sudo nvidia-glx-config enable and I get this an output:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.



Help?

---

### Post by PriceChild on 2006-12-09
I reckon you should do as it tells you:
```
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
```

---

### Post by zeroooooooooooo on 2006-12-09
Well, now I did that, and then when I tried to reboot X, it gave me an error screen saying that xorg.conf was configured incorrectly and had to use the command 

cp /var/backups/xorg/xorg.conf.2006-12-09-16:21:57 /etc/X11/xorg.conf 

to use the backup. 

Suggestions?

---

### Post by igknighted on 2006-12-09
you can edit xorg.conf manually.  type:
```
sudo nano /etc/X11/xorg.conf
```
and search for the line "Section "Device"".  There should be a line that says "driver 'nv'".  Change the 'nv' to 'nvidia'.  Then hit ctrl+'o', enter, and then ctrl+'x' to save and exit.  Finally, hit ctrl+alt+backspc to restart x.  It should load with the nvidia splash screen before x loads.

If something should go wrong, you will be dropped into a text terminal.  Simply type the same thing as above, find section "device" again and change 'nvidia' back to 'nv' and then restart.

---

### Post by zeroooooooooooo on 2006-12-09
Thanks a lot, that worked.

---

