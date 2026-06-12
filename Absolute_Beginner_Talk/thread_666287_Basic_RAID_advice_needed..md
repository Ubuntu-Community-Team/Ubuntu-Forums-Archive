---
title: "Basic RAID advice needed."
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by erkswede on 2008-01-13
Hi all

I have an Ubuntu 7.04 feisty fawn server up and running well. Now I want to add two 300 GB disks in a RAID 1 array for secure storage. The system is installed on a single 20GB disk and I intend to keep this as is.

There is a "fake raid" controler, Promise pdc20276, on the MB and I have installed the two disks on the IDE slots (IDE 3 and 4). 

As I see it I have two options.
1. Using the fake raid controller and configure ubuntu accordingly or
2. Use a software raid solution.

Are these my options or am I going about this the wrong way?

Do I need to to have the pdc20276 controller enabled in the MB BIOS if go with option 2? that is, will ubuntu recognize the two disks without the controller enabled?

I have no desire to use the fake raid controller other than that I initially thought this would be the simplest. No I know better... ;-)

The goal here is to have some reliable storage for a few clients on my LAN.

Thanks
/Erik

---

### Post by Malta paul on 2008-01-13
Hi, If you wish to use a RAID hard disk system with Ubuntu, you will need to install it using the alternate CD disk.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)   
Have a look at this video for more info:
[http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2](http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2)
Hope this helps you :)

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-13
> **Malta paul said:**
> Hi, If you wish to use a RAID hard disk system with Ubuntu, you will need to install it using the alternate CD disk.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)   
Have a look at this video for more info:
[http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2](http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2)
Hope this helps you :)

I think you maybe incorect about haveing to install using the alternate CD, becuses your just adding storage and the system stuff is not going to be on the raid drives.
now that i have said that i have no idea how to get it working :)

---

### Post by Malta paul on 2008-01-13
Just for info. the setup for a RAID HD system means you have to do a manual format and select the type of raid system you require to use ( RAID 2 is normally used).
Of course there may be another way which I don't know of! :guitar:

---

### Post by erkswede on 2008-01-13
You're right joe, just adding storage. System is already ok on a single disk. I just need some help to choose the right path. Thanks any way.

---

