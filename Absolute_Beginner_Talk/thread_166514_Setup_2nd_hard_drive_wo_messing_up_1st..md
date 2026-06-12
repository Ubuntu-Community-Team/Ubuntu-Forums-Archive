---
title: "Setup 2nd hard drive w/o messing up 1st."
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Ichido on 2006-04-26
I have a Desktop with Linspire/Linux Factory Installed.
I have Installed a new 40GB hard drive (drive-2), but I have not yet Partitioned or Formated it.
I want to install Ubuntu & Kubuntu on the drive #2 (40GB), due to Linspire has consumed all of Drive #1.
Can I Install Kubuntu & Ubuntu onto drive-2 without messing up GRUB on Drive-1?
Do I need GRUB on both drives?
Any help would be great.

---

### Post by confused57 on 2006-04-26
This thread may help, check the advice by lha, maybe just change the title to Ubuntu instead:

[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)

On your second hd, you may want to install Ubuntu, then install kubuntu-desktop after installing Ubuntu.

---

### Post by Ichido on 2006-04-26
There is a lot of good info at that link, but I don't see how it applies to my situation.
Linspire uses GRUB, and it works fine.
Linspire does not need a swap partition, it just 'sucks-up' my whole drive-1!
I want to Install Kubuntu without messing up my Linspire O.S. or it's GRUB.
Can I use Ubuntu & Kubuntu with the same install, just by 'switching' desktops?
I am new to Linux and I am very cautious.

---

### Post by aysiu on 2006-04-26
Yes, you can use Ubuntu and Kubuntu on the same install and just switch between Gnome and KDE.

Plug in your second hard drive and do the Ubuntu install. Select **Manually edit partition table** and then select /dev/hdb1 to be mounted as / and formatted as Ext3.

When you're asked where you want to install Grub, install it to /dev/hdb1 instead of the MBR.

Then, in Linspire, mount the Ubuntu partition and copy and paste the Ubuntu /boot/grub/menu.lst entry to Linspire's /boot/grub/menu.lst

---

### Post by Ichido on 2006-04-26
Thanks.
Hopefully I will get time to do this this weekend.

---

