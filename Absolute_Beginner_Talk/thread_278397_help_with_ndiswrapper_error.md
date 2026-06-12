---
title: "help with ndiswrapper error"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by pregoeater on 2006-10-16
hello im trying to make my onbaord wi-fi work i have broadcom 4306 im following the instructions here  [http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306)

when i get to the part with  "sudo modprobe ndiswrapper"   i get this error



FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

if anyone could help me that would be great its not a huge deal because i have another wi-fi card that does work but its b not g so i would like the braodcom to work

thanks 
pre

---

### Post by wondering_jew on 2006-10-17
I had the same problem. For me the issue was with the ndiswrapper available in the repositories. 

Try removing ndiswrapper with 
sudo apt-get remove ndiswrapper-utils ndiswrapper-common

Then follow Step 2 and 3 Here [http://ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g](http://ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g)

substituting your driver where appropriate
remember to do a
   sudo depmod
and a
   sudo modprobe ndiswrapper

---

