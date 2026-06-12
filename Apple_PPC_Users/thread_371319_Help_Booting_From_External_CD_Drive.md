---
title: "Help Booting From External CD Drive"
date: 2007-02-26
forum: Apple PPC Users
---

### Post by DisgruntledPostMan on 2007-02-26
I have a Powerbook G3 Lombard "bronze keyboard" and The Built in Cd drive wont read my burnt cd.  My workaround to this was to attach one of my external cd drives and install the drivers.  It worked and Ubuntu_PowerPc_Edgy appeared on the desktop, I was able to browse through the files on the disc and I then tried to boot from the external cd drive.  I pressed "C" to boot from the cd but it did not work.  I have tried with the built in drive taken out with the same result.  Upon booting from firmware I write boot cd:,\\yaboot but it says it can't open the disc.  Is there a way to boot to an external device in the firmware, or is there a way to install from the disc while Os 9 has booted, any help is appreciated.

Trying to install Edgy Eft, System is running 9.2.2

Thanks in advance.

---

### Post by didg on 2007-02-26
At least one issue is that the cd alias is still pointing to your internal drive.

cf bug.  [https://launchpad.net/ubuntu/+source/yaboot/+bug/35731]("https://launchpad.net/ubuntu/+source/yaboot/+bug/35731")

---

### Post by DisgruntledPostMan on 2007-02-26
Thank you.  I will look into that.  I'll post details in a min.

I'm booting from a usb drive.

What would be the OF path?

---

### Post by didg on 2007-02-26
It's machine dependent.

cf.[https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html")

---

### Post by Bubbles7031995 on 2007-03-02
I have this same problem! I have a powerbook G3 Pizmo, my CD drive doesn't read anything but I do have an external CD drive... I haven't tried holding down the "c" key though. If anyone helps you, they will be helping me to! If I find anything that might work for you, I'll let you know.

---

