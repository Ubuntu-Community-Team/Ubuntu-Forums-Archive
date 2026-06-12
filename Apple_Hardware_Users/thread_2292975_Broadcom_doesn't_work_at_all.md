---
title: "Broadcom doesn't work at all"
date: 2015-09-01
forum: Apple Hardware Users
---

### Post by Austin_Muckelrath on 2015-09-01
I installed Ubuntu on my MacBook Air and I noticed that the internet (which I have broadcom) doesn't work at all. It worked when I demonstrated it on my USB flash drive, but not when it's installed via dual-boot. 

Is there an driver issue that I'm not aware of? Keep in mind, I can't connect to the internet and my MacBook Air doesn't have an Ethernet built-in.

---

### Post by crystalocean on 2015-09-01
Hi Austin,

Try plugging back in and mounting the USB you used to install Ubuntu and then open up your file manager.

Then, navigate to two different locations:

First, navigate to /media/cdrom/pool/main/b/b43-fwcutter and install what is located there.

Second, navigate to /media/cdrom/pool/main/d/dkms and install what is located there, too.

Now, try connecting to the internet again and please report back on what happens!

---

### Post by Bucky Ball on 2015-09-01
Quicker and easier if possible, get online with a cable if you can, update, and check in 'Additional Drivers' if you are not offered a driver first. Also, please post the output of this:

```
sudo lshw -C network
```

Thanks. That will tell us exactly which Broadcom chip you have and what driver, if any, is currently installed.

It's a bit of a catch 22 that sometimes you need to get online with a cable to get online with wireless. The cable is redundant once you're up and running on wireless, off course.

PS: When you install a new driver you will probably need to pull the cable out to see if it worked. You may also need to reboot (boot with cable out). Good luck.

---

