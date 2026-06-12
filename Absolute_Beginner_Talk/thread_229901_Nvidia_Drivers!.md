---
title: "Nvidia Drivers!"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by weightgain4000 on 2006-08-05
Hello,

I am having some problems updating my Graphics card drivers! I would like to use the latest ones!

Ive looked at two guides now and neither of them has worked for me!

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

This works right up till

sudo nvidia-glx-config enable

Then I get the following error!

john@Ubuntu:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
john@Ubuntu:~$

I then tried this suggestion

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

I used Shabba's Post but found nano wasnt a very user friendly programs for a novice!

so I only got to this point

sudo nano /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Can someone please give me some clear instructions on how to make this work!

Thank you for your time

John

---

### Post by _simon_ on 2006-08-05
I've used METHOD 1 here more times than I can remember on different machines and it's always worked:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by weightgain4000 on 2006-08-05
Great worked like a charm!!!!!!!!!!!!!! :D

---

### Post by _simon_ on 2006-08-05
Great! now bookmark it or print it out in case you need it again - will save you time! :)

---

### Post by tseliot on 2006-08-05
sudo nvidia-glx-config enable is broken

Do this instead:
```
sudo nvidia-xconfig
```

and next time please follow the guide which _simon_ suggested

---

