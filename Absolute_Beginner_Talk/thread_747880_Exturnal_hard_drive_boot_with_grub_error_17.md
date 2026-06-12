---
title: "Exturnal hard drive boot with grub error 17"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by lcc.joshua on 2008-04-07
Exturnal hard drive boot with grub error 17.

I am trying to install 2 kinds of linux on my 250GB exturnal hard drive.
Ubuntu 7.10  and Fedora 8.

I fallowed these instuctions so far, and i got a Grub error 17.

Please help.



A complete Ubuntu install to a USB hard drive is a relatively simple process. As a matter of fact, it is almost as simple as a regular Ubuntu internal hard drive or compact flash card installation. Due to popular e-mail demand from our subscribers, we have decided to write a simple tutorial on the Ubuntu USB hard drive installation procedure. So go grab an available external USB hard drive and a nice cold beverage and lets get started.
Notes: Do be forewarned that this is a full installation (not a compressed Squashfs install) so you don't want to do this on a USB flash pen*drive. Only an external USB or Firewire drive with a rotating platter.
Full install Prerequisites:
8 GB + USB hard drive (note "rotating platter" we aren't talking about a*flash drive*here) 
Backup any information on your USB hard drive (device will be formatted during the install process) 
Ubuntu ISO (Ubuntu 7.04 was used in this tutorial) however 7.10 should work as well 
CD Burner 
Installing Ubuntu to an external USB hard drive:
1.IMPORTANT: Ensure that all internal hard drives are disconnected from your computer during the install (pull your SATA or IDE cables) 
2.Download the Ubuntu 7.04 ISO, burn it to a CD and restart your computer from the live CD 
3.Once the Ubuntu Live system is up and running, navigate to System-> Preferences-> Removable Drives and Media and uncheck the following options: 
Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted
4.Click the install Ubuntu icon from the desktop to begin the installation 
5.At step four Prepare disk space, select the Guided-use entire disk option and elect to install to your USB hard drive: 

6.When the installation has finished, select the option to restart-now 
7.Boot into your system BIOS or Boot Menu and elect to boot from your USB Hard drive. 
If all goes well, you should now be booting into a full installation of Ubuntu from your portable USB device.

---

### Post by zvacet on 2008-04-07
[Here](http://users.bigpond.net.au/hermanzone/p15.htm#In_a_computer_with_more_then_one_hard)

---

