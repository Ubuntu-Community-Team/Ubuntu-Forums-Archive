---
title: "Linux Mint 13 recognizes HP LsrJet1100(with parallel to usb cable)but does not print"
date: 2012-11-07
forum: Any Other OS
---

### Post by martinmace on 2012-11-07
Hi guys,

after a long search on the web i'm giving up and i do not see any reason why the mentioned printer is not printing(not even the print test page)! 

lpstat -a gives me:
```

HP-LaserJet-1100 accepting requests since Wed 07 Nov 2012 03:19:02 PM CET

```
and lpq gives me
```

HP-LaserJet-1100 is ready
no entries

```

i even can see that the printer has been recognized in the printers gui. i'm using a parallel to usb adapter with the specification USB910 from a no-name trademark. 

any suggestions? 

martin

---

### Post by martinmace on 2012-11-07
btw, if i plug the cable and let me give out a list in the folder /dev I can see the device
ttyUSB which I won't see when the cable is not plugged in, so the adapter has been recognized, doesn't it?

[EDIT:as well as 
dmesg|grep ppdev gives me
```

[   17.523361] ppdev: user-space parallel port driver

```

and lpstat -t:
```

scheduler is running
system default destination: HP-LaserJet-1100
device for HP-LaserJet-1100: usb://HP/LaserJet%201100
HP-LaserJet-1100 accepting requests since Wed 07 Nov 2012 04:18:56 PM CET
printer HP-LaserJet-1100 is idle.  enabled since Wed 07 Nov 2012 04:18:56 PM CET
	Waiting for printer to become available.

```

---

### Post by Elfy on 2012-11-07
*Thread moved to **Other OS/Distro Talk**.*

---

