---
title: "Attempting triple booting on a macbook with no success, need help"
date: 2009-01-05
forum: Apple Hardware Users
---

### Post by WA_Garrett on 2009-01-05
Hello, I'm attempting to set up my macbook to be able to boot OS 10.4, Ubuntu, and Windows XP. I shrunk my Macintosh HD partition and freed up unpartition free space for the 2 other operating systems. I have installed rEFIT, I have not used boot camp.  I am still able to boot from OS X, but I cannot boot from Ubuntu or XP after trying to install them. 

Upon booting from the XP disk to install it, when the partitioner came up, windows did not register the free unpartitioned space on my hard drive I set aside, just a singe "C" drive that was roughly the size of my entire HD. I had to abort installing XP. 

Upon booting from the Ubuntu CD, I was walked through the set up process until I came to the partitioner, which registered my Macintosh HD and the unpartitioned free space I made, it also displayed some fat-32 partition that is 200 MB and 2 "free space" partitions that are at the begging and end of the list that were 0 MB in size. I took the free space assigned some room for the Ubuntu partition, some swap space for Ubuntu and I assigned the rest  as a fat-32 partition hoping Windows would get the hint to go in that partition when I tried to install it again. I continued, Ubuntu did it's partitions and seemed to write its operations system files fine. After installation it asked me to reboot, which I did, I booted from the Ubuntu partition, the screen flickered, and then displayed this message "no bootable device -- please insert boot disk and press any key to continue" upon inserting the Ubuntu boot disk and pressing any key the system was unresponsive. Ubuntu doesn't boot from my hard drive, but I was able to run it from the live CD just fine. 

I tried installing windows again after I created the fat-32 partition, but it had the same problems. 

I want to know if anyone knows how to get Windows and Linux onto a macbook and is willing to provide some suggestions, or if anyone is trying to do this same thing and is having the same problems as I am so we can bounce ideas back and forth.

---

### Post by cyberdork33 on 2009-01-05
Lots and Lots of info here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

When asking for support with your hardware, please be sure to mention the version of your Mac. You can see the information in the "Before You Post" link in my signature to determine your Mac version and find the appropriate documentation for you mac.

---

### Post by tnjed111 on 2009-05-17
Where did you install grub to? I installed it on the Ubuntu partition and it works fine, but when I accidentally installed it elsewhere I got an error like you're getting.

---

