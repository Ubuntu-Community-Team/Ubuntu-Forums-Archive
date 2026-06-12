---
title: "sudo dpkg-reconfigure xserver-xorg"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by xstation on 2005-12-05
My system boote up after adding some packages.

and it was with black  screen with white letters  under tty1
login

I tried cntrl alt F7 no joy

startx   no joy

I then ran sudo dpkg-reconfigure xserver-xorg

I filled all the different options and after the last one the flashing curser returnre4d at the the foot of the last message. with a warning above the
the flashing cursor


xserver-xorg postinst warning
overwriting possibly customised config etc/x11/xorg.conf.back-up
in 200512031024

I do not type anything and exit only to find myself with the same black screen  tty1 login screen when I reboot (as mentioned at 
start of message)

Is there something I should then type at command prompt after reconfig xserver-xorg has finished?


andy:???: :???:

---

### Post by ScreemingBlue on 2005-12-05
Try > startx again.

---

### Post by az on 2005-12-05
Did your graphics card ever work, or was this the firs time you booted?  What kind of graphics card do you have?

---

### Post by xstation on 2005-12-05
I installed  5-10 a week ago and worked since then I added some packages but when deleting python I expect more was deleted than I bargined for.


startx gives me a gretyish screen with a with arrow head which I able to 
move about thats it. 

When my system was running I never tried the startx comand.

andy:???:

---

### Post by xstation on 2005-12-05
my graphics card is ati readon 9100 

andy:???:

---

### Post by darkmatter on 2005-12-05
[QUOTE=xstation]but when deleting python[/QUOTE]

Python is rather heavily integrated in Ubuntu...removing it is not a good thing.

Boot in to failsafe (rescue mode) and after login, try:

```
sudo apt-get install ubuntu-desktop
```

once it is installed...reboot. That will reinstall the desktop and any dependencies ... and should help you on your way to getting up and running... not the cleanest way... but unless you know EXACTLY what packages you removed... it's about the easiest.

---

### Post by xstation on 2005-12-06
Thanks darkmatter wored fine, I will be more careful next time

andy:smile:

---

