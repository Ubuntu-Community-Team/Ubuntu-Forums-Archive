---
title: "turning off ndiswrapper"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by xxrealmsxx on 2006-06-14
I have a broadcom wireless card on my zv6000 laptop and I have gotten the cards drivers to work.

However I was wondering if there is any way for me to check if currently ndiswrapper is running also, reason being is that my wireless internet connection is really buggy and I am trying to figure out if i am having any sort of conflict or if the broadcom drivers for ubuntu just suck.

Its not showing up under processes so i am assuming ndiswrapper is not running.

Thanks in advance.

---

### Post by xxrealmsxx on 2006-06-14
[QUOTE=xxrealmsxx]I have a broadcom wireless card on my zv6000 laptop and I have gotten the cards drivers to work.

However I was wondering if there is any way for me to check if currently ndiswrapper is running also, reason being is that my wireless internet connection is really buggy and I am trying to figure out if i am having any sort of conflict or if the broadcom drivers for ubuntu just suck.

Its not showing up under processes so i am assuming ndiswrapper is not running.

Thanks in advance.[/QUOTE]


I believe I answered my own question:

root@jamiewitter-laptop:/home/jamiewitter# ndiswrapper -l
No drivers installed

---

### Post by az on 2006-06-14
[QUOTE=xxrealmsxx]I believe I answered my own question:

root@jamiewitter-laptop:/home/jamiewitter# ndiswrapper -l
No drivers installed[/QUOTE]
Correct.  But ndiswrapper is a kernel module and not a process.  To see if it is being used, run

lsmod

But since there are no drivers installed, it will not associate with any device.   I think.

---

### Post by xxrealmsxx on 2006-06-14
[QUOTE=azz]Correct.  But ndiswrapper is a kernel module and not a process.  To see if it is being used, run

lsmod

But since there are no drivers installed, it will not associate with any device.   I think.[/QUOTE]

thanks, lsmod does not show it.

Is there anyway to restart a kernel module?

---

### Post by Jagot on 2006-06-14
I think it would be :

```
sudo modprobe [module_name]
```

---

### Post by xxrealmsxx on 2006-06-14
[QUOTE=Jagot]I think it would be :

```
sudo modprobe [module_name]
```[/QUOTE]

ok thanks!

now to see if that helps when my internet goes whacky.

---

### Post by az on 2006-06-14
[QUOTE=xxrealmsxx]thanks, lsmod does not show it.

Is there anyway to restart a kernel module?[/QUOTE]
I don't think so.  For example, If you unload a module, I am not sure that you can then compile a new version of it and load it cleanly without having to reboot.

If I wanted to be sure that the kernel module was properly restarted, I would put the new on in place (on the disk, /lib/modules/2.6.15....) and then reboot.  I would not try to remove it an reinsert it.

The same would go for any hardware it was trying to control.  If I load a module that takes charge of my wireless card, I would not assume that I could unload that module and then load ndiswrapper and it would then take charge of the hardware properly.  I would unload, blacklist and then reboot.  I'm sure some modules would handle this cleanly, but I cannot be sure of all kernel modules.

---

