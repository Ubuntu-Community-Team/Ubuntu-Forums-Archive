---
title: "MacBook keyboard not working after suspend"
date: 2019-12-22
forum: Apple Hardware Users
---

### Post by samuelcho on 2019-12-22
Dear all,
I am using an early 2008 black MacBook on Ubuntu 18.04 with Xubuntu Desktop Environment. After a suspend, my keyboard is not working properly. The P key outputs *, the / outputs + and a few other keys output other symbols.

What DOES work however: the arrow keys work fine, volume keys and eject keys work too. The trackpad works. Using a USB keyboard works as well (with which I am using to type this). 

A little background: 
I recently updated from 16.04 LTS to 18.04 LTS. I know it's a bit old, but my machine is old too and I wanted to try an older distro first. After updating, the keyboard and wifi both stopped working. I have tried

[COLOR=#000000]sudo apt-get install --reinstall xserver-xorg-input-all

[/COLOR]This did not change anything. I tried many solutions, some of which involved reconfig-ing the keyboard (involving selecting the layout, language). I don't remember the command anymore but this did not work immediately as well. So with less success, I tried fixing the wifi, which was only a problem of the system not being able to convert URL's to DNS addresses. After fixing wifi, the keyboard, for some reason, began working. 

Now, after suspending, the keyboard stopped working again (the wifi is still working) and I'm not too sure what has changed in the system. I am not sure if I have given enough info, but should you guys need more info for debugging, I would gladly give them. Thank you!

[COLOR=#000000]

[/COLOR]

---

### Post by howefield on 2019-12-22
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by samuelcho on 2019-12-22
Update: I have logged out of Xubuntu and started a normal Ubuntu session. Now everything works fine. Is there a reason why XFCE/Xubuntu does not work with this keyboard?

---

