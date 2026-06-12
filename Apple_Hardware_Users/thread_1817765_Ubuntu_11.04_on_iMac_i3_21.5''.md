---
title: "Ubuntu 11.04 on iMac i3 21.5''"
date: 2011-08-03
forum: Apple Hardware Users
---

### Post by ekktha on 2011-08-03
Here is the iMac that I use
i3 3.1GHz
4Gb DDR3
Video ATI HD4670 256Mb

I have tried to install Ubuntu 11.04 and have achieved after a long day with many helps from many links. I think maybe this can save somebody time.

1. install "rEFIt" on Mac : [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

2. resize the Mac partition by using Boot Camp or Disk Utility and then delete the new partition that you have created , or you can delete it when installing Ubuntu.

3. Download alternate version of Ubuntu 11.04 from : [http://cdimage.ubuntu.com/releases/11.04/release/](http://cdimage.ubuntu.com/releases/11.04/release/)
I used the "64-bit Mac (AMD64) alternate install CD" version. And burn CD out of this .iso file.

4. Restart and to boot from CD, when start up mac hold "c" to activate boot from cd before it run rEFIt. Or you should see the options in rEFIt to boot from Ubuntu cd, you can also use this way.

5. Install Ubuntu without live version. I have tried several distribution live version and it couldn't start up at all, so here install Ubuntu directly. 

6. In the partition setup page choose "Manual" at the last line and choose free space that you have deleted. Or if you have not yet deleted new drive that you want, then delete it here.

7. After that choose "auto create partition" on this free space. Ubuntu will create 3 partitions for you first for Grub boot loader, second for root (/) and the last for swap partition. And PLEASE remember the name of partition that you have created for Grub for example "/dev/sda4", you need it in next step. ***Important here to have the first partition for Grub because if you don't have this and install it in first partition with OsX then you won't be able to start osx again. In my case I have to reinstall to get boot sector back. The methods that using disk utility in osx install cd didn't work for me. So please be aware of this!!

8. After install everything then in the step of install Grub, it will tell you that it won't be able to install Grub in target partition and let you choose it. Problem here is that the list of partition shown are not the correct partition for Grup, that why you have to take note in previous step. Here give the correct name, normally it should be one number before the last choice that Ubuntu gave you. Ex. the last one is "/dev/sdc5" and the correct one that is not shown should be "/dev/sda4" with different part "sda4" and "sdc5"

9. Then It can be installed and reboot and in "rEFIt" you can see penguin for Ubuntu dive on it. Works are not yet done here since we still have problem of "Graphic driver of ATI". So the next step is what you need.

10. In Grub menu choose recovery section of Ubuntu and press "e" to edit and give additional option "readeon.modeset=0 nomodeset" after the line like
"linux   /boot/vmlinuz-2.6.32-18-generic root=UUID=fcf85719-2242-4b65-a162-a41060902f45" and it must be directly after this in the SAME LINE not in the separate line. Save it and then reboot.

11. If everything correct here you should be able to see Ubuntu screen here, with some options choose "low graphic mode" to enter it.

12. Then install the driver by typing 
$ sudo apt-get install fglrx
$ sudo aticonfig --initial
$ sudo reboot

Then every thing should work here you can choose the normal boot in grub menu after choose to boot Ubuntu from rEFIt menu. 

Have fun!!!, Hope this help.

---

### Post by JustinAlf on 2011-10-11
> **ekktha said:**
> 

10. In Grub menu choose recovery section of Ubuntu and press "e" to edit and give additional option "readeon.modeset=0 nomodeset" after the line like
"linux   /boot/vmlinuz-2.6.32-18-generic root=UUID=fcf85719-2242-4b65-a162-a41060902f45" and it must be directly after this in the SAME LINE not in the separate line. Save it and then reboot.


Edit: it needs to be "radeon.modeset=0 nomodeset"  \

You mispelled it.

Other than that, you have an outstanding fix that worked for me!

---

