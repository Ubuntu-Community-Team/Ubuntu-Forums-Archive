---
title: "[SOLVED] Wifi working on Macbook Pro 8,2 on Ubuntu 12.04"
date: 2012-05-26
forum: Apple Hardware Users
---

### Post by raritan01 on 2012-05-26
I can't take all the credit, but this is what I did to get my bcm4331 to be recognized in Ubuntu 12.04.

Got these instructions from Tim Hentenaar's Blog and tweaked them a bit
[http://hentenaar.com/serendipity/index.php?/archives/2012/05.html](http://hentenaar.com/serendipity/index.php?/archives/2012/05.html)

Run the following in the terminal:
$ sudo apt-get install b43-fwcutter firmware-b43-installer
$ sudo dpkg-reconfigure firmware-b43-installer
response from terminal:
$ No chroot environment found. Starting normal installation
$ Unsupported device(s) found: PCI id 14e4:4331 
Aborting.

then run:
$ sudo modprobe b43
$ export FIRMWARE_INSTALL_DIR="/lib/firmware"
$ cd ~\Downloads
$ wget [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2) $ tar -xjf broadcom-wl-5.100.138.tar.bz2
$ sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" broadcom-wl-5.100.138/linux/wl_apsta.o

You'll get a response like this:
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e

...and a lot of extracting will happen

Then enter:
$ dmesg | tail -2

You'll get a response like this:
[ 5866.172626] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5870.282827] applesmc: FS! : read arg fail

Then just enable/disable wireless in Network Manager and it works!

---

### Post by wildmanne39 on 2012-05-26
Hi, thank you for posting your solution this will help a great many people.

---

### Post by wildmanne39 on 2012-06-19
Hi, please try:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Reboot
Thanks

---

### Post by Baulageng on 2012-06-20
Thank you for giving me this information ... it will help me a lot and other people also..........

---

### Post by eatfoodnow on 2012-08-18
Thank you so much! Worked like a charm.

---

### Post by vampyrjang on 2012-08-20
Thank you so much, you saved lot of my time. It really helped me.

---

### Post by Ijonti on 2012-12-03
This also worked on my Mid-2012 Macbook Pro 9.1 (which was giving me the exact same error message). Thanks very much!

---

### Post by oconn88 on 2013-01-10
Thanks a lot for this, I have spent the past 5 hours reading forums. This was the only one I have come across that actually worked on my MBP 9,1.

---

### Post by LinuxBill on 2013-01-10
Thanks, going to try this when i get home from work. Hopefully its solves my problems. Only just installed on my 8,1 macbook pro using refit.
 
EDIT: This worked perfectly for me thanks a bunch!

---

### Post by Tony_Barry on 2013-09-20
This worked with my MBP 8,1 running Ubuntu 12.04 LTS.  Took about one day to find this answer.  Thanks to raritan01.

Regards,
TB

---

### Post by Tony_Barry on 2013-09-20
> **Tony_Barry said:**
> This worked with my MBP 8,1 running Ubuntu 12.04 LTS.  Took about one day to find this answer.  Thanks to raritan01.

Regards,
TB

Unfortunately the fix did not persist after a reboot.  Any ideas from the gurus ?

Regards,
TB

---

### Post by stinstin on 2014-03-09
Thank you so much after one day to try, it work for me.... You perfect (Macbook pro 8.1)

---

