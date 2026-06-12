---
title: "Wireless driver help"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by imacbo on 2007-03-31
Ok I still need some help with my wireless. This has been such a pain in my butt!!
So here is the low down. My computer has a built in Broadcom 4318. I also have a PC card called Edimax 7608Pg (which came with the linux driver RT61). I have tried to install a Broadcom 4318 driver with ndiswrapper to no avail. The directions that came with the Rt61 dont make sence to me. So here is the direstions for the Edimax using a Ralink RT61 driver.
For 2.6 series kernel:
a.  run 'cd STA/Module'
        'cp ../2.6x/Makefile .'

b. $make all

c. $cp RT2561.bin /etc/Wireless/RT61STA/	# copy firmware
   $cp RT2561S.bin /etc/Wireless/RT61STA/
   $cp RT2661.bin /etc/Wireless/RT61STA/
   
d.  run '/sbin/insmod rt61.ko'  (as root)
        '/sbin/ifconfig ra0 inet YOUR_IP up' 


For big endian platform:
a.  replace Makefile with Makefile.RTL865x

When I try to run the STA it dont work. I can not get past the first command. Now can someone show me in newbie step-by-step. Or would it be better to try the 4318 Broadcom? And could someone help with that in step-by-step newbie as well. Thanks a lot guys.

---

### Post by chili555 on 2007-03-31
The command is:```
cd STA/Module
``` cd means 'change directory' and you will change to the directory where you extracted the .tar.gz file you downloaded.

Did you see this? I especially loved seeing the word "Solved":[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

---

### Post by imacbo on 2007-03-31
When I run the cd /STA it says that STA is not a vaild dir

---

### Post by chili555 on 2007-03-31
It's not /STA it's STA. Those are different.

Please go to Places -> Home Folder. Is the folder that got created when you extracted the tar.gz in there? Is it called STA?

The command:```
cd STA/Module
```means 'change directories to STA and then to the directory inside STA called Module.' Please try again.

---

