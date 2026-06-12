---
title: "No Gui"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by ubuntokun on 2007-11-21
I recently adjusted my resolution to one higher than the normal 1024 and now when I boot ubunto I hear the start up  sounds but i'm not seeing anything but a black screen. How can I fix this problem. Can it be done from a command line? Please I really miss my Ubunto.:( I NEED HELP!!
__________________

---

### Post by taurus on 2007-11-21
Why even create second post when you already have two replies in your original post?  :roll:

[http://ubuntuforums.org/showthread.php?t=619261](http://ubuntuforums.org/showthread.php?t=619261)

---

### Post by oneadvent on 2007-11-21
Please keep threads together:

[http://ubuntuforums.org/showthread.php?p=3812101&posted=1#post3812101](http://ubuntuforums.org/showthread.php?p=3812101&posted=1#post3812101)

---

### Post by Inxsible on 2007-11-21
Login to the recovery mode and then type in```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then simply reboot.
Remember, however, that you will need to re-install the restricted drivers, if you use any, after you do this.

---

