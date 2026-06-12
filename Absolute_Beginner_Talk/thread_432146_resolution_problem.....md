---
title: "resolution problem...."
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2007-05-03
I installed ubuntu 7.04 beta amd64. It is up to date. My grafic card is nVidia 7900gt and driver version is 1.0-9755. I have allso instaled Beryl..... Now.... Every time I restart or shut down my pc, screen resolution resets to 1600x1200.. My monitor is Samsung Syncmaster 797df and nvidia x server auto detects it. So.. after restart I must every time manualy set res to 1280x1024!!!!!! :confused: 
It starts to be very annoying...  I would like to set it permanently to 1280x1024. Any ideas... thx!

---

### Post by freebird54 on 2007-05-03
I don't have nVidia - but here are a few thoughts...

Do you have the System->Preferences->Screen Resolution set to 1280x1024, and chosen as default?   Do you have 1280x1024 as the 'highest' setting in /etc/X11/xorg.conf ??  Do you have a line in your /boot/grub/menu.lst entry for booting that sets the vga mode?  (see list here)

```
Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?
```

You can set vga=795 on the startup line - if nothing else has worked.  I also thought there was a nvidia-settings program of some kind - does that not allow for forcing a default?

Hope something here helps... :)

---

### Post by _mOrgoth_ on 2007-05-03
Thx!!! It helps a lot:lolflag:

---

