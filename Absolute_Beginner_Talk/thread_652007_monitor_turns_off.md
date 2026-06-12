---
title: "monitor turns off"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-12-28
i have just installed Gutsy Gibbon, and have installed the nvidia driver from System > Administration > Restricted Drivers (or something like this). ok, installation worked fine but now, after restarted, when booting - the monitor turns off, even though it can be heard in the background the system login sounds ... any ideas?

p.s. i have nvidia geforce fx 8500 gt and have downloaded the nvidia driver from nvidia.com but a friend told me i can install it from that place i've told you... and so i did :(

---

### Post by overdrank on 2007-12-28
> **the_nomad said:**
> i have just installed Gutsy Gibbon, and have installed the nvidia driver from System > Administration > Restricted Drivers (or something like this). ok, installation worked fine but now, after restarted, when booting - the monitor turns off, even though it can be heard in the background the system login sounds ... any ideas?

p.s. i have nvidia geforce fx 8500 gt and have downloaded the nvidia driver from nvidia.com but a friend told me i can install it from that place i've told you... and so i did :(

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and you can use the command ```
startx
``` or use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by the_nomad on 2007-12-28
thanx so much! it worked and now im back on Ubuntu :) i have noticed that after the monitor turns off and ubuntu reaches to the login screen, if pressing enter or moving the mouse the monitor turns on again!

thanx a lot man, i owe you!\\:D/8)

---

### Post by overdrank on 2007-12-28
> **the_nomad said:**
> thanx so much! it worked and now im back on Ubuntu :) i have noticed that after the monitor turns off and ubuntu reaches to the login screen, if pressing enter or moving the mouse the monitor turns on again!

thanx a lot man, i owe you!\\:D/8)

Ok great and if you keep having issues you may look a Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
And could you mark the thread as solved under thread tools. Good luck!

---

