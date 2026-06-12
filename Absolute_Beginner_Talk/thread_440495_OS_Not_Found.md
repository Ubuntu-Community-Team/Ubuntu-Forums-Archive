---
title: "OS Not Found"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Tommy22 on 2007-05-11
I'm brand new to Ubuntu and having trouble with installation. I downloaded the image and installed Ubuntu. I rebooted the computer like it said but as it was booting i got an error saying the operating system was not found. Please Help!!!!

---

### Post by dangerpl on 2007-05-11
Did you follow any specific directions while installing? What was your previous system? How did you format your drive?

---

### Post by Tommy22 on 2007-05-11
I followed the instructions from the installer

---

### Post by danmpem on 2007-05-11
I had a similar problem.  I have a computer with two hard drives, one master and one slave.  I installed Ubuntu on the master hard drive, but when I would reboot, the GRUB boot loader wanted to boot the slave hard drive.  I turned off my slave hard drive inside the BIOS menu, and then reinstalled Ubuntu on my master hard drive.  Once that was able to boot, I turned my slave hard drive back on, and now everything works great!

I have no idea if that's even close to what you're talking about, but I hope that helps someone! =)

---

### Post by Tommy22 on 2007-05-11
well i have two scsi hard drives. i installed Ubuntu on the second one. I have the Bios set to load from scsi but it wont specify which on its booting from.

---

### Post by carlosqueso on 2007-05-11
I don't know if this is the case, but if you installed ubuntu to the back part of a large disk, it may not boot.  Try putting a /boot partition further up on one of the disks if you can.

---

### Post by Tommy22 on 2007-05-11
I dont know were it was installed i just followed the guide.

---

### Post by Tommy22 on 2007-05-11
I just reinstalled and now it works fine. thanx

---

