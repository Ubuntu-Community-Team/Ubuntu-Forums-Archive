---
title: "Scanning"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-07-12
Oh man oh man..........I could use my scanner before now no way.
Epson Perfection 2480 photo.
Now I get error 
Failed to open device ' snapscan:libusb:005:002': Error during device I/O
It was working before.. but so many upgrade...... I wonder ?  :confused:

---

### Post by yabbadabbadont on 2007-07-12
What is the output when you run in a terminal window: ```
ls -lR /dev/bus/usb
```

---

### Post by burt_57 on 2007-07-13
/dev/bus/usb:
total 0
drwxr-xr-x 2 root root  60 2007-07-13 05:46 001
drwxr-xr-x 2 root root  80 2007-07-13 05:47 002
drwxr-xr-x 2 root root 100 2007-07-13 05:47 003
drwxr-xr-x 2 root root  60 2007-07-13 05:46 004
drwxr-xr-x 2 root root  80 2007-07-13 05:46 005
lrwxrwxrwx 1 root root  14 2007-07-13 09:47 devices -> .usbfs/devices

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root 189, 0 2007-07-13 05:46 001

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root    189, 128 2007-07-13 05:46 001
crw-rw-r-- 1 root scanner 189, 129 2007-07-13 05:47 002

/dev/bus/usb/003:
total 0
crw-rw-r-- 1 root root 189, 256 2007-07-13 05:46 001
crw-rw-r-- 1 root root 189, 257 2007-07-13 05:47 002
crw-rw-r-- 1 root root 189, 258 2007-07-13 05:47 003

/dev/bus/usb/004:
total 0
crw-rw-r-- 1 root root 189, 384 2007-07-13 05:46 001

/dev/bus/usb/005:
total 0
crw-rw-r-- 1 root root    189, 512 2007-07-13 05:46 001
crw-rw-r-- 1 root scanner 189, 513 2007-07-13 05:46 002
robert@robert-desktop:~$

---

### Post by yabbadabbadont on 2007-07-13
Do you have two scanners attached?  It looks like devices 002:002 and 005:002 are both scanners.  Anyway, it looks like it should work if your user is a member of the scanner group.  In a terminal window, run "id" without the quotes and see if scanner is one of the groups listed.  If it isn't, in a terminal window, run ```
gpasswd -a yourusername scanner
``` and then logout and back in and see if it then works.

---

### Post by burt_57 on 2007-07-13
> **yabbadabbadont said:**
> Do you have two scanners attached?  It looks like devices 002:002 and 005:002 are both scanners.  Anyway, it looks like it should work if your user is a member of the scanner group.  In a terminal window, run "id" without the quotes and see if scanner is one of the groups listed.  If it isn't, in a terminal window, run ```
gpasswd -a yourusername scanner
``` and then logout and back in and see if it then works.

One scanner...... but guess what?
Ubuntu does not work anymore.
I will have to reinstall it.
I have try twice now to reinstall but no luck.
I have done the fmbr.
All was well , just windows came up.
But as far as reinsatlling Ubuntu Ultimate....... no way it will not work.
Will give another try  when I have finish formatting the second drive, and checking it 
for errors..... darn it. :confused:

---

### Post by burt_57 on 2007-07-13
Ok after 8 hrs off trying to reinstall Ubuntu Ultimate I decided to install Ubuntu I/386.
My printer work now so is everything else.
Guess what ......... I can see my 2 monitors now !
The only thing is to figure out how to use them independent from one to another, 
I mean independent to each other .
Like Monitor 1 and monitor 2 .
I don't want to span. :lolflag:

---

