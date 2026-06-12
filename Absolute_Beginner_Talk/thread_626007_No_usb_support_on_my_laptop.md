---
title: "No usb support on my laptop"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by abedbajia on 2007-11-28
i just installed ubuntu on my laptop hp dv9500 (gusty gibbon)

after a rough experience i got some of the stuff to work (the ones i need)

but when i inserted the a usb flash drive ubuntu didnt read it'
so i wonder is there a driver for usb support 

plzz i need the usb to work
thanks

---

### Post by Pumalite on 2007-11-28
What's the format?

---

### Post by Threbus5 on 2007-11-29
I understand that Ubuntu supports NTFS or Fat32 formatted usb drives.
Check the usb format.
Try another usb drive or another usb port.

For plan "B", install the previous Ubuntu version, Feisty, that performs differently.

---

### Post by abedbajia on 2007-11-29
the proble is that when i run lsusb in terminal the terminal freezes

so i guess that usb has an errors and i dunno how to fix any advice

thanks

---

### Post by JimmyBEng on 2007-12-11
I was running into a similar problem with my laptop.  It was caused by an error loading the uvcvideo during startup.

you can tell if this is the case by running
```
dmesg
```

if you are having the same problem you will find an error with a stack trace after where modprobe tries to load those modules (see attached file for what this looked like on my computer)

----------------------------------
If this is your problem here is how to fix it.
open the blacklist file
```
gedit /etc/modprobe.d/blacklist
```
and add the following to the file
```
## causes error with ricoh 1812 webcam that disables USB
blacklist uvcvideo
```

This prevents the uvcvideo module from loading.  On mine this loading error was tying up the USB so that no other devices could make use of it.

Hope this helps.

---

### Post by JimmyBEng on 2007-12-11
here is the file with the error that i mentioned.  Forgot to attach it before.

---

### Post by JimmyBEng on 2007-12-11
abedbajia i just saw your other post also about disabling bluetooth.  that was the first problem i ran into and for me was actually caused by the uvcvideo error.  If the above fix works for your laptop, you should be able to enable bluetooth again.

---

