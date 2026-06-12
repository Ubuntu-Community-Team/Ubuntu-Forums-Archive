---
title: "Monitor Issue prevents startup"
date: 2012-02-16
forum: Apple Hardware Users
---

### Post by rlinsurf on 2012-02-16
I can't start because I'm getting the following output, and then it just sits there. Anyone know what's going on here?

[IMG]http://dhnet.us/images/ubuntu_errorl.jpg[/IMG]

I'm running on a Mac Pro5,1 with an Apple 23" Cinema Display.

---

### Post by gordintoronto on 2012-02-16
What version of Ubuntu? Dual-boot? If you still have Mac OS, what does DisplayConfigX show? What cable? No bent pins in the connectors?

---

### Post by rlinsurf on 2012-02-16
I don't know because I can't get into it, but I ran all the updates to my 10.x version sometime in September.

DisplayConfigX says:

Name: LED Cinema Display 
ID: 610=APP 
Model: 9226

Card: ATIRadeonX3000
Driver: 1.6.36.10
Memory: 512 MB

The Cable is a dual-link DVI port, with the monitor in one of the ports, and no it's all in perfect shape.

---

### Post by rlinsurf on 2012-02-17
Sorry, I was wrong. It's in the mini DisplayPort. 

Also, when I try starting up now, I just get a black screen. 

Help!

---

### Post by rlinsurf on 2012-02-17
I had some more wrong information. This is Ubuntu 11.x, not 10.x.

---

### Post by rlinsurf on 2012-02-17
Ok, I just tried to reinstall the whole OS from the LiveCD. The install went fine, but when I tried to reboot into the OS, I got the same black screen, this time with a blinking cursor and nothing else.

---

### Post by rlinsurf on 2012-02-17
I just tried to run the 11.10 installer again, and this time checked everything. When doing the partitioning, I checked for any messages and I got: I-I-1: probed a monitor but no|invalid EDID. 

I also read it might be where I'm installing grub, but I don't see the Advanced options on the LiveCD like they used to be. Can someone tell me how to install grub?

---

### Post by gordintoronto on 2012-02-17
Grub is automatically installed. Is it possible to try a different cable/connector? Do the computer and the monitor both have DVI, for example?

---

### Post by rlinsurf on 2012-02-17
Maybe that's the issue. This is a partitioned drive with a Lion volume as well as the swap and the ext4 which I was trying to install on. If I select the ext4 partition in the partition manager, is that where Ubuntu and grub go?

Perhaps this maybe a Lion problem? I installed lion after I was already running Ubuntu successfully, maybe that's what screwed it up?

---

### Post by rlinsurf on 2012-02-17
Oh, sorry. No, it just has the one mini DisplayPort out.

---

