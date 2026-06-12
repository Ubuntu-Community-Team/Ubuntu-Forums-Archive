---
title: "Following Tails Live USB installation instructions, I get &quot;Permission Denied&quot; error"
date: 2012-04-09
forum: Any Other OS
---

### Post by distribution on 2012-04-09
So I'm trying to create a Live USB to boot [Tails]("https://tails.boum.org/index.en.html") but I can't seem to get past this permission denied error. I've tried using sudo, but I keep getting denied. The group has [instructions on installing Tails]("https://tails.boum.org/doc/installing_onto_a_usb_stick/linux/index.en.html") to create the boot disk that I've followed closely. There is also a troubleshooting section at the bottom which has my exact problem with no clear solution. What should I do to get the necessary permissions?

I'm running Ubuntu 11.10 and I'm trying to install Tails 10.2.

---

### Post by oklokl on 2012-04-09
ubuntu 11.10 x32 x64
Distributor Manager
 This is a bug ... (current)

sudo fdisk -l

umount -l /dev/sdc1

sudo apt-get install gparted

create

or
remove..
sudo dd if=/dev/zero of=/dev/sdc bs=446 count=12345

or..

testing
badblocks test..
mount
sudo badblocks -v /dev/sdc1

or
umount -l /dev/sdc1
sudo badblocks -vw /dev/sdc
(long time.. )

fast format
sudo mkfs.vfat /dev/sdc1

---

### Post by flurospar on 2012-04-09
You might want to use Unetbootin to do a live USB install.

---

### Post by Elfy on 2012-04-09
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by distribution on 2012-04-09
So I followed the troubleshooting steps again and it worked out. I did 

sudo su -

and ran it again. It worked. Thanks for all the advice guys.

---

### Post by Steve6375 on 2012-12-11
You can boot Tails from an ISO - see [http://www.rmprepusb.com/tutorials/tails]("http://www.rmprepusb.com/tutorials/tails")

---

