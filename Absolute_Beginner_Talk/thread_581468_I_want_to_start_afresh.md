---
title: "I want to start afresh"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by shavedchimp on 2007-10-19
Hi everyone

I've been given a laptop and want wipe Windows off it and install Ubuntu.

There's no data on the laptop I want to keep. I've got the latest Ubuntu, got the CD burning software and the winMd5sum software.

Once I've burned the CD - where do I go from here? I presume I need to format the hard disk on the laptop, then reboot with the Ubuntu CD in the drive - is that right?

How do I format the hard drive?

Any help appreciated

Thanks

shavedchimp

---

### Post by Phil Airtime on 2007-10-19
You don't need to format the HDD before you reboot. The Ubuntu install CD will take care of that for you; select "Guided, use entire disk" and it'll format and partition the disc for Linux.

If, when you reboot with the CD in the drive, your PC boots Windows from the hard disc, take a look in your BIOS (usually Delete or F2 during boot, look for the instruction) and find the "boot device priority" setting.

---

### Post by dward526 on 2007-10-19
Yes, Ubuntu will take care of the formating for you.

Before you do this, go into windows and check to see what devices you have using Device Manager.  Pay special attention to the wireless driver.  Linux should support most of your hardware natively, but its support for wireless is touchy.  If your new install recognizes the wireless, all is right with the world.  If it does not, there are tools you can use like 'madwifi' and 'ndiswrapper' (I used that one on this computer right now).  Knowing what your hardware is before hand is very useful in this situation.

---

