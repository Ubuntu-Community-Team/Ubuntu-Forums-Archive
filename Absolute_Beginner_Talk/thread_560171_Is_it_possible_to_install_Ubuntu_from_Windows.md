---
title: "Is it possible to install Ubuntu from Windows?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by srinathtk on 2007-09-26
Dear Friends,

Thanks for all your help in solving our PC problems.

I have a AMD Athlon 3000+ processor, AS Rock motherboard with 80GB of SATA+40 B of IDE HDD, 1.5 GB DDR1 RAM, SATA DVD Writer with Windows XP professional.

Now I am interested in installing Ubuntu Linux software and created a seperate 15GB partition on my IDE hard disk using Partition magic.

I got a bootable Ubuntu DVD to install the OS. Now I am facing a peculiar problem. My system is not being booted from DVD drive and it is going to HDD only whenever I boot. 

To change the config to boot from DVD, I tried the following.
1. While system is booting, I pressed F11, it went to boot sequence menu. But the DVD is not listed in that and 1 floppy drive and 2 HDDs are listed in that.
2. I typed F2 after rebooting and opened the Bios Setup. In the 'Boot' tab, I could see only 2 options a)DVD and B) HDD. By default the option was first HDD and next DVD.
I modified the sequence to DVD and then HDD. Pressed F10 to save and exit. Again rebooted the system keeping the bootable DVD in the Drive but the system booted from HDD only.

I need help to solve this problem. Can any one help me sorting this out. Whether do I need to reinstall some drivers or Bios etc.

Is there any option to install Ubutu from Windows (without booting from DVD)?

Please help me.

Advance thank you.

Regards,

Srinath
India

---

### Post by rsambuca on 2007-09-26
My guess is that you burned the CD (DVD in your case) incorrectly.  For instructions on how to properly burn the installation disc, see this [link.]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by bodhi.zazen on 2007-09-26
Yes, but it may be difficult ...

[http://wubi-installer.org/](http://wubi-installer.org/)

On this link : [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) ; there is a section on installing without a CD.

[http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive](http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive)

[http://ubuntuforums.org/showthread.php?&t=316093](http://ubuntuforums.org/showthread.php?&t=316093)

---

### Post by overdrank on 2007-09-26
> **srinathtk said:**
> Dear Friends,

Thanks for all your help in solving our PC problems.

I have a AMD Athlon 3000+ processor, AS Rock motherboard with 80GB of SATA+40 B of IDE HDD, 1.5 GB DDR1 RAM, SATA DVD Writer with Windows XP professional.

Now I am interested in installing Ubuntu Linux software and created a seperate 15GB partition on my IDE hard disk using Partition magic.

I got a bootable Ubuntu DVD to install the OS. Now I am facing a peculiar problem. My system is not being booted from DVD drive and it is going to HDD only whenever I boot. 

To change the config to boot from DVD, I tried the following.
1. While system is booting, I pressed F11, it went to boot sequence menu. But the DVD is not listed in that and 1 floppy drive and 2 HDDs are listed in that.
2. I typed F2 after rebooting and opened the Bios Setup. In the 'Boot' tab, I could see only 2 options a)DVD and B) HDD. By default the option was first HDD and next DVD.
I modified the sequence to DVD and then HDD. Pressed F10 to save and exit. Again rebooted the system keeping the bootable DVD in the Drive but the system booted from HDD only.

I need help to solve this problem. Can any one help me sorting this out. Whether do I need to reinstall some drivers or Bios etc.

Is there any option to install Ubutu from Windows (without booting from DVD)?

Please help me.

Advance thank you.

Regards,

Srinath
India

Hi and welcome, I agree with rsambuca if you burned the dvd and if you would like to install from windows you can check out this link
[http://wubi-installer.org/](http://wubi-installer.org/)
You may also look at other ways of installation of Ubuntu
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Good luck!

Edit I have got to work on my typing skills to slow again!

---

### Post by WakkiTabakki on 2007-09-26
Go check out WUBI ([http://wubi-installer.org]("http://wubi-installer.org"))!
It allows you to install Ubuntu from within windows, and furthermore, without the need to repartition the harddrive.
It creates an image file in your windows partition to which it installs itself...

Good luck
/N

---

