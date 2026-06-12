---
title: "I have tried everything, still no wireless!!!"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by JCasper on 2008-05-03
So frustrating... I know this is supposed to be easy, but I can not get this to work. I have tried the tutorials on the community site, and every other site I have found and still no wireless.

I have a 2008 macbook and need some help :(

Thanks guys.

---

### Post by cyberdork33 on 2008-05-03
please indicate that you are using an Intel Mac in your thread titles from now on. This makes it easier for people to help you.

you will have to give more information. What have you done? how do you know it doesn't work? What about it doesn't work?

The output of these comamnds will help:

ndiswrapper -l

ifconfig

---

### Post by JCasper on 2008-05-04
Yes, sorry, 2008 macbook - intel C2D

OK, I originally tried to follow the community ubuntu tuts. Then I found out I had a broadcom and not an atheros wifi card. So then I tried to work with ndiswrapper and got to the command:

sudo modprobe ndiswrapper

Which gave me an error saying directory non existing or something. I will boot back into linux tomorrow morning and get those reports you asked for.

Thanks.

---

### Post by Bubba64 on 2008-05-04
I had a lot of problems getting the wireless to work in Hardy with manual configuration in the network manager then I set it to roam clicked on my personal link and put my wep key in with the correct wep type and it worked great.

---

### Post by MTZeon on 2008-05-04
Follow this guide and it will work for 2008 macbooks :)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by wepalm on 2008-05-04
I had this same problem.  It might be different for me because I am on a first gen macbook but it still might work.  My laptop did not detect a card at all.  There was no card there according to Ubuntu.  What I did to fix this is i went into the package manager and added the Recomended Updates for Gutsy repository:

Type:         Binary
URL:          [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
Distribution: gutsy updates
Components:   main restricted

I added these two packages:
1)        linux-restricted-modules-2.6.22-14-386
2)        linux-restricted-modules-2.6.22-14-generic


Afterwards I just restarted my macbook just to be safe and bam I had wireless.

---

### Post by cyberdork33 on 2008-05-04
> **JCasper said:**
> Yes, sorry, 2008 macbook - intel C2D
You need to follow the santarosa instructions. the guide you had was for earlier versions.

[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)

BTW, I was saying to add it to the thread TITLE. not in the body of the post. Nothing you can change about this one now, but please remember in the future.

---

### Post by JCasper on 2008-05-04
OK, thanks for all the suggestions guys. I am working at it, but I got the same error following the santarosa tut. I am using 64 bit version ubuntu if that helps.

jcasper@laptop:~$ cd driver/DRIVER/
jcasper@laptop:~/driver/DRIVER$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
jcasper@laptop:~/driver/DRIVER$ sudo ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present
jcasper@laptop:~/driver/DRIVER$ sudo ndiswrapper -m
module configuration already contains alias directive

jcasper@laptop:~/driver/DRIVER$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

Here is the ifconfig you asked for before cyberdork.

jcasper@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:5b:f2:a5:24  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:5bff:fef2:a524/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60943199 (58.1 MB)  TX bytes:2712000 (2.5 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75500 (73.7 KB)  TX bytes:75500 (73.7 KB)

THANKS GUYS!!!!

---

### Post by JCasper on 2008-05-04
wepalm, would I need those gutsy modules if Im in hardy?

---

### Post by JCasper on 2008-05-04
SUCCESSSSSSSSSSSS...FOR NOW... Fresh reinstall of ubuntu and I followed mtzeon's link and the thing freakin worked. Thanks so much man, I read on that site that a guy had trouble connecting to WPA, but mine seems to be up and going...THANKSSSSSSSS

---

