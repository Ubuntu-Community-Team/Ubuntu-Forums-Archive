---
title: "Major Minor Numbers in the Device Manager"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by thegurr on 2007-11-09
At the moment I'm trying to get an Iomega 250 USB set up.  I've been following the tutorial on this thread:
[http://ubuntuforums.org/showthread.php?t=12074](http://ubuntuforums.org/showthread.php?t=12074)
I  I think I've followed everything up to step 8:

> 8. Tell Ubuntu to create a device node manually during each boot-up by hacking another file - sudo gedit /etc/udev/links.conf . You will need to add a line that looks similar to this -

# Manually create a zip device.
M hdd4 b 22 64

What this line stands for is ' M(ake) hdd4 (a) b(lock device with major number) 22 (and minor number) 64' (your device name, major and minor numbers may differ from mine, of course) . The major and minor numbers for hd*4 are listed under your zip drive's entry in Device Manager (Advanced tab). Once you have the details, insert your line in /etc/udev/links.conf using the syntax above.

 but am stumped at the Major Minor numbers.  I'm in the device manager looking at my Iomega 250 USB advanced tab and don't know which numbers I'm supposed to be looking at.  

Not sure if it makes a difference but I'm using 7.10 gutsy gibbon.  Any info would be much appreciated.

---

### Post by PointyWombat on 2007-11-11
Hi thegurr,

You should see two values for 'block.major' and 'block.minor'.

also, check the /dev directory and see if there are existing devices for hdd.

PointyWombat

---

