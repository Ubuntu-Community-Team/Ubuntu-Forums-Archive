---
title: "X server error for wubi"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by tototime on 2007-12-01
Hello all i have a problem with wubi
something to do with an xserver error it says my graphics isnt set correctly has anyone had this problem and been able to fix it
also it wont let me boot into ubuntu it stays on boot screen

---

### Post by overdrank on 2007-12-01
> **tototime said:**
> Hello all i have a problem with wubi
something to do with an xserver error it says my graphics isnt set correctly has anyone had this problem and been able to fix it
also it wont let me boot into ubuntu it stays on boot screen

Hi when you receive the error click ok until you reach the command prompt then Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by tototime on 2007-12-01
when i click ok it says error with microcode it has failed to load and it does it over and over and wont boot up

---

### Post by overdrank on 2007-12-01
> **tototime said:**
> when i click ok it says error with microcode it has failed to load and it does it over and over and wont boot up

Ok then I have not used Wubi but you may look here
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)
I would even say post anew thread here. good luck! :KS

---

