---
title: "virtualbox and vista .. i cant use USB flash disk"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by DO55 on 2008-01-20
first i have this error
> Could not load the Host USB Proxy Serviceb

so i fix it by adding this to /etc/fstab
> none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0
[http://ubuntuforums.org/showthread.php?t=598390&highlight=the+Host+USB+Proxy+Service](http://ubuntuforums.org/showthread.php?t=598390&highlight=the+Host+USB+Proxy+Service)

now i can found USB option  in the virtualbox setting
i select my flash disk from the menu and make active 

when i run vista  the small usb icon in the virtualbox frame show its not active and when i move the cross over it it give me this messege
> no usb device attached 


---

### Post by nonewmsgs on 2008-02-17
mount it as a shared drive in virtual box settings on the screen before you boot that OS and it shuold work. 

if you are unsure of how to do that, just ask again and ill (or some other person will)certainly help.

---

