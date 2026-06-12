---
title: "Opening 6800LE pipelines in boot with nvclock"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by LaLLi on 2006-01-17
I bought a 6800LE because it was as cheap as a 6600 and with Rivatuner discovered its full potential. I managed to open all 16 pipes and 5 vertex units. I'm not too eager in modifying my GPU bios to get the full potential in use with Ubuntu. To my joy I found out that nvclock 0.8b enables the opening of these pipes just like in Rivatuner..well almost.

The problem is that I'd like this to happen automaticly during bootup. I'v been searching the net for an solutio and init.d seems like an option but I'v been unsuccesful in making the right script.

Please help..I need detailed instructions in the contents and installation of a proper script.

---

### Post by endy on 2006-01-17
Okay, this should be pretty straight forward. Here's what I would do:

Create a new file in /etc/init.d/ for example /etc/init.d/local
```
sudo gedit /etc/init.d/local
``` 
Paste in the comand line you want to run and save the file.

Make the file executable
```
sudo chmod +x /etc/init.d/local
``` 
Make it so it loads at boot time:
```
sudo update-rc.d local defaults
``` 
Reboot to make sure it works.

If you ever wat to stop if from loading on boot the following command shoudl do the trick:
```
sudo update-rc.d local remove
```

---

### Post by LaLLi on 2006-01-18
Didn't work. :(

I did what you told me and this is my /etc/init.d/nvpipes file

[I]#! /bin/sh

/usr/bin/nvclock -f -P 1111
/usr/bin/nvclock -f -V 111110
/usr/bin/nvclock -f -n 400 -m 800 -b lowlevel[/I]

Still no change.

EDIT: I found this in nvclock forums, should I include these command in my script or what?
*The pipeline changes will revert aswell. To unload the nvidia kernel module use 'rmmod nvidia' and to load it again 'modprobe nvidia'. I would recommend loading nvclock for pipeline modding from a startup script but before the nvidia drivers are launched (or else atleast when you are outside X)*

EDIT2: Tried something I found on Gentoo forums.
[I]#! /bin/sh
rmmod nvidia
/usr/bin/nvclock -f -P 1111
/usr/bin/nvclock -f -V 111110
modprobe nvidia[/I]

It didnt work. I tried to do it manually
Ctrl+Alt+F1
/etc/init.d/gdm stop
rmmod nvidia
/usr/bin/nvclock -f -P 1111
/usr/bin/nvclock -f -V 111110
modprobe nvidia
/etc/init.d/gdm start

Cant get past rmmod nvidia..it just says "Error: module in use" or something like that.

---

