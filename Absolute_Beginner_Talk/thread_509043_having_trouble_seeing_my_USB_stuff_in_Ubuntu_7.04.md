---
title: "having trouble seeing my USB stuff in Ubuntu 7.04"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by skhobotu on 2007-07-24
When I connect anything to my USB, sometimes it will come up and sometimes it won't. I use a program called 
Storage device manger and all my settings are auto,user and this usually works, but they don't come up in Computer as a mounted device that I can unmount. How can I clean this up so my devices mount each time and can be unmounted?
I installed Storage Device manager because none of my USB devices would come up under Ubuntu. But now it sometimes says that the device No-Name can't be mounted OR You have no permission to mount this device when I reset the permissions to default. Then the next time it comes up on screen as soon as I plug it in, but not in Computer. AAAAAAAGGGGHHHHH!!!!!!

[http://pastebin.com/d5e5eac5d](http://pastebin.com/d5e5eac5d) shows my /etc/fstab file

---

### Post by FleetAdmiral74 on 2007-07-25
With the drive plugged in, enter lsusb and dmesg, that might provide useful information.

---

### Post by skhobotu on 2007-07-25
The problem is solved.
[http://pastebin.com/m1b53fb3a](http://pastebin.com/m1b53fb3a) to see my new fstab file.
What was happening was that Automatix had created another mount point and it was conflicting with my main USB mount point /media/fash. Once I deleted the mount point created by Automatix using the Storage Device Manager, I could load any of my USB devices, except my camera card which is SD and I know from the forum that SD is not supported under Linux. But I don't need to be able to store 1125 photos on my card, 50 stored on the internal hard drive in fine resolution is more than enough for me! I'll give the card to the teenagers.

---

