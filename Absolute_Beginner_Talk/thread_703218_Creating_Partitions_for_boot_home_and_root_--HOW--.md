---
title: "Creating Partitions for /boot /home and /root --HOW?--"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2008-02-21
I am using Ubuntu 7.04 and I want to upgrade to 7.10.  I am using Ubuntu only so I do not want it to work with Windows as well.  Just want to know how to do it and how it works so I can upgrade to 7.10.

---

### Post by timbosity on 2008-02-21
I think I read somewhere that with hardy there was going to be some nifty way of upgrading and keeping your /home safely where its at. I also think I have read that upgrading from feisty to gutsy has a few little niggles and a clean install is a good option. If you were to do a clean install from a live CD you can backup your /home to another CD or something and when it comes to creating your partitions choose manual and make your /home  et al. partitons. Then just copy your backed up files back on to the /home partition. I did it that way after my first tinkering around, although I went from gutsy to gutsy...

---

### Post by FrozenFox on 2008-02-21
Your post is a little strangely worded, so forgive me for asking questions that you may think are clear. You have ubuntu currently installed and want to update it.. if it's currently installed, why do you need to worry about the new partitions? Do you just want to make a new separate /home account instead of your current setup that is all the same partition for home and root?

If you just want to upgrade your stuff, if I recall correctly, you should just be able to sudo apt-get dist-upgrade in the console and reboot when it's done.

---

### Post by buntu_Geek on 2008-02-21
Upgrading can be done using the update manager...

I did upgrading to 7.10 Gusty from Feisty.... No probs for me....

By saying upgrading to 7.10 means upgrading each and every app u have installed in your previous feisty to its gusty equivalent made... even the kernel itself gets upgraded to the latest version.... :D

You can just see the change while installing 7.10 after downloading the required packages....

But i heard there are certain problems after upgrading ...

This site list the problems....
[http://shaneosullivan.wordpress.com/2007/10/18/upgrading-ubuntu-feisty-fawn-704-to-gutsy-gibbon-710/](http://shaneosullivan.wordpress.com/2007/10/18/upgrading-ubuntu-feisty-fawn-704-to-gutsy-gibbon-710/)


Check this HowTo :

[http://www.howtoforge.com/upgrading_ubuntu_7.04_to_7.10](http://www.howtoforge.com/upgrading_ubuntu_7.04_to_7.10)

Hope that helps you...

---

### Post by justleen on 2008-02-21
to move the partitions:

- create a new partition (with fdisk of gparted). Make a note of the device name (eg /dev/dsa8)

- create a temp root dir
```
 sudo mkdir /media/temp_root 
```

- mount the partion on this temp folder
```
 sudo mount /dev/sda8 /media/temp_root 
```

- copy the contents of /root to the new partition (-r for recursive, -v for verbose)
```
 sudo cp -rv /root/* /media/temp_root
```

- umount the drive
```
 sudo umount /media/temp_root
```

- remove the old root folder (be very carefull!! )
```
sudo rm -rf /root 
```

- edit /etc/fstab to reflect the changes
```
 sudo nano /etc/fstab
```
you should add 
```
 /dev/sda8  /root  ext3    defaults  0 0
```
save and exit

- mount the new partition as /root
```
 sudo mount -a
```

---

### Post by Brendan Hart on 2008-02-21
Ok but I'm not sure what partitions I have already... I just did a clean install of 7.04 using full hard drive, and when upgrading the guide said its a good idea to use seperate partitions, and never told me how to set partitions and if my computer had already made partitions.


ALSO: i dont have sda8 I got sda1

---

### Post by FrozenFox on 2008-02-21
It's a good idea to use a separate /home partition in order to save your data in case something bad happens to your system or that particular partition of your hard drive. It's not a necessity though. You should be able to dist-upgrade to gutsy, but it comes with a few problems as some have said. Your best bet may indeed be to copy your data, format, and then find a quick guide on manual configuration of partitions for ubuntu, there's lots of them around. Some people prefer not to do it that way, though, as just dist-upgrading would work.

---

### Post by Brendan Hart on 2008-02-21
> **FrozenFox said:**
> It's a good idea to use a separate /home partition in order to save your data in case something bad happens to your system or that particular partition of your hard drive. It's not a necessity though. You should be able to dist-upgrade to gutsy, but it comes with a few problems as some have said. Your best bet may indeed be to copy your data, format, and then find a quick guide on manual configuration of partitions for ubuntu, there's lots of them around. Some people prefer not to do it that way, though, as just dist-upgrading would work.

My software should be fine i'm sitting on a base installation

---

