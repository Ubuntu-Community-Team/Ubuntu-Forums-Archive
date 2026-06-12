---
title: "My graphics are slow on Edgy Server"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Matodo on 2007-02-04
Hello

After installing Ubuntu 6.10 Server and the modem driver, I've installed ubuntu-desktop.
My graphics card is ATI Radeon 9250.
Everything is slow. I have to wait several seconds until I can move a window, maximize it,... I can't even scroll down without the need to wait 5 seconds.
I have followed [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b"), but after restarting xorg, my X server didn't start. So I had to delete the modification that I did.
This is the first time that I have such a problem with Ubuntu. I have already used Dapper and Edgy, everything was fine. I haven't had to install any kind of drivers.
Please help, I can't use Ubuntu if this problem isn't fixed.

Thanks in advance.

---

### Post by annda on 2007-02-04
do you use ati or radeon driver at the moment?

( you can find the info in /etc/X11/xorg.conf )

---

### Post by Matodo on 2007-02-04
Well, I have uninstalled the fglrx driver, and restored the backup of the xorg file.

---

### Post by shareMenaPeace on 2007-02-04
Did that fixed it?

And how much ram does the computer have, maybe its just not enough to run the desktop.

---

### Post by Matodo on 2007-02-04
> Did that fixed it?
No
> And how much ram does the computer have
512 MB
> This is the first time that I have such a problem with Ubuntu. I have already used Dapper and Edgy, everything was fine. I haven't had to install any kind of drivers.

---

### Post by annda on 2007-02-04
if you had a working system before installing the binary ati driver, you have to undo ALL the steps you did and not just revert to the old xorg.conf file.

---

