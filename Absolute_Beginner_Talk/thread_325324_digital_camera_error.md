---
title: "digital camera error"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2006-12-25
im trying to import pictures from my digital camera in ubuntu (fluxbox) and I get the following error when importing

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

---

### Post by zetsumei on 2006-12-25
no one has a clue to what i can do to fix this, all the other topics do not relate to my problem...

---

### Post by iitywygms on 2006-12-25
I have the exact same problem.  I am using edgy with a canon sd800.
I did some research and found this link which sounds close to our problem.  I am not at that computer right now so I can't tell you if it works.
[http://www.ubuntuforums.org/showthread.php?t=290205&highlight=digital+camera](http://www.ubuntuforums.org/showthread.php?t=290205&highlight=digital+camera)
Hopefully it works for you and me.

---

### Post by iitywygms on 2007-01-03
I have not had any luck getting this to work.  I also noticed that my camera locks up when I connect it to the computer.   It is a cannon sd800.  Anyone have any ideas?

---

### Post by harerama on 2007-01-03
Hi there,

I got exactly the same problem and haven't fixed the problem yet.

The thing is that before I installed the Edgy my camera worked totally fine on Dapper.

It started to Not function after I moved to Edgy after that I moved back to Dapper again and it doesn't work anymore.

Right now when I plug my camera into my computer. Nothing happens at all.

Anyone? Please.

My thread can be find here
[http://ubuntuforums.org/showthread.php?t=329684&highlight=digital+camera](http://ubuntuforums.org/showthread.php?t=329684&highlight=digital+camera)

Cheers.

---

### Post by goonies on 2007-03-16
same prob, my thread is here

[http://ubuntuforums.org/showthread.php?t=385505](http://ubuntuforums.org/showthread.php?t=385505)

---

### Post by luc_o on 2007-03-23
I had this problem too, probably after an automatic update.
This worked for me:
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)
(change line 3 in the file /etc/udev/rules.d/45-libgphoto2.rules)

---

### Post by Blutack on 2007-03-23
Same for me, I used both the line 3 thing AND [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)
That fixes it

---

### Post by kwas101 on 2007-03-30
This forum TOTALLY ROCKS!:guitar: 
Fixed my error too, must have been after an upgrade since it only stopped working since last weekend...
Thanks once again everyone :KS :KS :KS :KS :KS

---

### Post by Neurowiz on 2007-05-25
This bug/comment thread is what fixed the issue for me with my Canon SD800:
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)

I did the following:
1. lsusb | grep Canon
*Bus 005 Device 009: ID 04a9:3136 Canon, Inc.*

2. sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
(added as the last in the list)
*SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3136", MODE=="0660", GROUP="plugdev"*

3. Restarted udev:
*/etc/init.d/udev restart*

My libgphoto2.rules already had the "usb_device" line in it.

Regards.

---

### Post by Zeals on 2007-07-12
[ATTACH]38002[/ATTACH]

Hi im getting the above dialog box coming up when I connect my canon powershot a430 via usb, have tried editing the gphoto2 file as suggested and went through the steps as suggested in the previous post, still no luck. Im using feisty. Any help would be appreciated. 

Thanks

---

