---
title: "Trouble connecting my cell phone to my computer"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Antarctica on 2007-01-02
Hey all, I received a Nokia 2865i for Christmas.  Today I bought the Nokia Connectivity Cable (a simple USB connection for my phone to my computer).  Anyway, I downloaded KMobileTools to transfer files between my phone and my computer (running Ubuntu 6.10 Edgy Eft).  I connected the cable and my phone displayed "Data Enhancement Connected."  KMobileTools displayed an error, so I tried turning on TTY/TDD and my computer froze completely.  I disconnected the cable and the computer was still frozen.  So, I rebooted and reconnected (with TTY/TDD still on) and the computer froze once again.  I rebooted a third time, and while Ubuntu was still booting, I connected the cable once more and the boot process froze.  I cannot seem to get my phone connected to my computer (which is pretty old anyways).  Does anybody have any suggestions?  Thanks.

---

### Post by MkfIbK7a on 2007-01-02
> KMobileTools displayed an error,

what was the error

---

### Post by Antarctica on 2007-01-02
The error displayed when KMobileTools starts up is "An error occurred while initializing mobile phone device.  Check your configuration and try again."

---

### Post by MkfIbK7a on 2007-01-02
well did you try to configure it through kmobile

---

### Post by Antarctica on 2007-01-02
I'm not exactly sure how to configure it.  Could somebody help me?

---

### Post by Antarctica on 2007-01-02
I unplugged the USB cable from the phone and plugged it back in.  I went into the terminal and typed dmesg.  The last lines of output are:

```
[ 5074.879140] ohci_hcd 0000:00:0d.1: wakeup
[ 5075.262791] usb 4-1: new full speed USB device using ohci_hcd and address 6
[ 5075.484847] usb 4-1: configuration #1 chosen from 1 choice
[ 5075.535959] drivers/usb/class/cdc-acm.c: Ignoring extra header, type -3, length 4
[ 5075.536025] cdc_acm 4-1:1.1: ttyACM0: USB ACM device
[ 5075.630615] rndis_host 4-1:1.11: RNDIS init failed, -110
[ 5075.630654] rndis_host: probe of 4-1:1.11 failed with error -110

```
I hope this helps any.

---

### Post by Antarctica on 2007-01-02
I found the device under /dev/ttyACM0.  KMobileTools is recognizing my phone now, but it's saying I have a low battery level, a low signal, and it won't import my contacts from my phone.  Is there any way to fix this problem?

---

### Post by Antarctica on 2007-01-02
Any solution?

---

### Post by Antarctica on 2007-01-02
There has to be a way to get my cell phone to work on Ubuntu.  I know something will work if somebody can point me in the right direction.

---

