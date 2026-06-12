---
title: "HOWTO: Install Gusty to a USB Hard Drive or Flash Drive"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by yamfox on 2007-12-28
This is the method I used:

1. Put disk in disk drive
2. Select "Start or Install Ubuntu"
3. Wait for it to start up.
4. When loaded up, go to System > Preferences > Removable Drives and Media and deselect the following options:

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

5. Connect the USB Hard drive or Flash drive
6. Press the Install link on the desktop
7. Go through the installation process as you normally would.
8. When the time comes for Partitioning, chose /sda1/ or something similar.   
9. Chose the partitioning options that you want (eg. create new partition, erase entire disk etc.)
10. Wait for the rest of the installation to finish.
11. Edit your BIOS so the order is
CD>USB>HARD DRIVE
12. After editing your BIOS, make sure the Ubuntu installation disk is taken out and reboot
13. You're done!!

You should now have a working USB Hard drive or Flash drive install
:guitar:

---

### Post by SOULRiDER on 2007-12-28
This should be in the Tutorials and Guides secttion.

Ive been wanting to install linux on a usb stick i have, ill follow this guide and tell you my results :)

---

### Post by Niniel on 2007-12-28
What do you do for swap space in the case of a USB stick? I don't think you'll want that on the stick itself.
You'll probably also want to switch off the various logging functions; it would be interesting and useful to get a list of those and how to deactivate them.

---

### Post by SOULRiDER on 2007-12-28
I was thinking and its probably better to use the alternate disc to install less features since the space in usb sticks is rather limited. I also agree witht he swap space comment, swap int he usb stick would be somewhat disastrous :P

---

### Post by anewguy on 2007-12-28
I'm also curious.  There are 2 things which have held me back from doing this:

(1) Aforementioned swap -- can't see it being on a slow device

(2) While improving, there is still a somewhat limited mtf on flash memory.  As a novelty this would probably be okay, maybe even for demo purposes, but I'd never run a regular environment off it.

---

### Post by yamfox on 2007-12-28
This is how I did it. I used the Seagate ST3120203U2-RK 
([http://www.newegg.com/product/product.asp?item=N82E16822148168](http://www.newegg.com/product/product.asp?item=N82E16822148168)) and it worked fine.

---

### Post by SOULRiDER on 2007-12-28
I would only install Ubuntu on a flash drive as an experiment actually, if I really wanted a distro to do that i'd get puppy or DSL

---

### Post by onthefence on 2008-01-31
I did almost the same thing, except I did not do step 4. Also, I'm not sure that I took the installation disc out when rebooting after install.
I got the following undesirable result:
The installation put GRUB on my laptop hard drive and configured it such that if the the USB flash drive is not inserted at boot it gives an error and will not show other OS's to load. 
Therefore now I cannot boot off my laptop hard disk unless the flash drive in inserted. 

My intention was to put everything on the flash drive so that it was entirely independent and I could launch it from any computer that allows a boot from USB, but such that it did nothing to my hard disk. I currently have Windows installed on my laptop.

I was very careful during the partition phase that the partitions it was installing to were on the USB flash drive only. For the record, I DID put the swap on the flash drive and it seems to work fine. It may not be as fast as it could be but it was definitely faster than the Live CD.

Also a couple of newbie questions that don't realy deserve their own post.
1. What is the best backup program available for Ubuntu?2. Where can I find and run GParted? It was available on the Live CD but I looked in the same place on the USB install and couldn't find it.

Thanks

---

### Post by Pelham123 on 2008-01-31
I installed 7.04, xfce & thunar on a corsair 4Gb mem stick. Didnt bother with any swap, but did make a custom iso and thinned out ubuntu. Seem to remember it being about 700mb (installed size) never noticed any real problems with performance, but then I just used it as a 'browser on a stick'

---

### Post by dcstar on 2008-01-31
It is absolutely bone-headed to do a "normal" install on any Flash based device, as these devices still have a finite quantity of write cycles and using them like a hard drive will just bring their failure date forward.

Most USB flash drives also have the big limitation of slow write speeds, both of these reasons are why there are HOWTOs on using these devices as "Persistent" Live devices (like the Ubuntu Live CD but the settings are saved on the USB) using a RAMDISK to minimise the performance limitations of the USB flash devices.

Do yourselves a favour and use them with the limitations of the hardware in mind:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

