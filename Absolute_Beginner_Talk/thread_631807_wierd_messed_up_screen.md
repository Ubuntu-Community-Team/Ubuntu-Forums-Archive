---
title: "wierd messed up screen"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by revilo62 on 2007-12-04
ok so i installed gutsy gibbon on my dell inspiron 8000 and it works great but the only thing is the screen is messed up it shows double kinda like the far left is the same as the middle (even the mouse doubles)
any ideas? if so email me at [email]Revilo62@yahoo.com[/email]

---

### Post by m0biu5 on 2007-12-04
Can you attach a screenshot and possibly the contents of /etc/X11/xorg.conf ?

---

### Post by overdrank on 2007-12-04
> **revilo62 said:**
> ok so i installed gutsy gibbon on my dell inspiron 8000 and it works great but the only thing is the screen is messed up it shows double kinda like the far left is the same as the middle (even the mouse doubles)
any ideas? if so email me at [email]Revilo62@yahoo.com[/email]

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by m0biu5 on 2007-12-04
There is no reason to reboot after editing your xorg.conf file (even through a wizard). If you restart GDM as mentioned, you should seem the same effect. Usually you can switch back to X using CTRL + ALT + F7 (although i've seen that number vary).

---

### Post by revilo62 on 2007-12-06
sounds good but the thing is i wont be able to answer the questions because the screen is so messed up i wont be able to see them... thx for the help and more would be appreciated

i have an idea but not sure if it will work so ill keep posting saying if it worked

---

### Post by revilo62 on 2007-12-06
ok well my idea didnt work but what i did do was try your ctrl alt f1 and i open up a thing i could see and all it did was ask for my pass again then i did the reboot command and it rebooted and it still has the same problem


here is a pic i took with cam (screen to messed up to do a screen shot) (first is log in screen and the other is the desktop)

[IMG]http://img457.imageshack.us/img457/9492/p1000552ou1.jpg[/IMG]

[IMG]http://img462.imageshack.us/img462/3239/p1000556lc1.jpg[/IMG]

---

### Post by revilo62 on 2007-12-07
so can no one help?

---

### Post by exactopposite on 2007-12-07
> **revilo62 said:**
> so can no one help?

i had the same problem. i fixed it with the info in this post:
[http://ubuntuforums.org/showthread.php?t=167670](http://ubuntuforums.org/showthread.php?t=167670)

---

### Post by revilo62 on 2007-12-07
> **exactopposite said:**
> i had the same problem. i fixed it with the info in this post:
[http://ubuntuforums.org/showthread.php?t=167670](http://ubuntuforums.org/showthread.php?t=167670)

wow it worked thx! the last post on the page the fn f7 one worked great i love it thx!

---

