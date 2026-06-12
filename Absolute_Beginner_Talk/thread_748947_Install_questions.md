---
title: "Install questions"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by lcc.joshua on 2008-04-07
I bought a 250GB WD usb exturnal hard drive, with the plans of booting 2 linux's.
Ubuntu and fedora each with 30GB hard drive space, and having the remanding drive space Fat32 so i can store data from my windows system on it.

I have installed Ubuntu 7.04 first with these directions.
Installing Ubuntu to an external USB hard drive(from this site [http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253):](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253):)

IMPORTANT: Ensure that all internal hard drives are disconnected from your computer during the install (pull your SATA or IDE cables) 
Download the Ubuntu 7.04 ISO, burn it to a CD and restart your computer from the live CD 
Once the Ubuntu Live system is up and running, navigate to System-> Preferences-> Removable Drives and Media and uncheck the following options: 
Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

Click the install Ubuntu icon from the desktop to begin the installation 
At step four Prepare disk space, select the Guided-use entire disk option and elect to install to your USB hard drive: 


When the installation has finished, select the option to restart-now 
Boot into your system BIOS or Boot Menu and elect to boot from your USB Hard drive. 
If all goes well, you should now be booting into a full installation of Ubuntu from your portable USB device. 


after I did all of this i got a grub error 17. 
I have burned a Grub super disk.
I have Ubuntu 7.04 live disk.

Please help.
Thanks,
Joshua L.

---

### Post by dstew on 2008-04-08
If you boot a Live CD, can you see the USB drive on your desktop?

---

### Post by adrian15 on 2008-04-10
> **lcc.joshua said:**
> 
after I did all of this i got a grub error 17. 
I have burned a Grub super disk.
I have Ubuntu 7.04 live disk.
Please help.
Thanks,
Joshua L.

If you have actually disconected hard disk when installing this external distro please reinstall it again but making sure that you use manual partitioning and set a /boot mount point  / partition of 300 MB size at the beginning of your drive.

Do not forget the / partition, the swap partition and maybe the /home partiton.

adrian15

---

