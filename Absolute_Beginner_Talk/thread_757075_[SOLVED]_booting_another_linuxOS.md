---
title: "[SOLVED] booting another linuxOS"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by waspbr on 2008-04-16
Hi there, 

I am running hardy dual booting with vista, all is fine, but I thought It may be a good idea to boot another linux OS along side, so if I mess up anything on one, I can always fix or edit something on the other. So I decided to install PCLinuxOS.

During the installation I decided not to install grub on the PCLOS partition since it never seems to detect my ubuntu partition, so rebooted. Apparently my grub does not detect the PCLOS partition, although it is very much installed. 

any pointers as to how I can add the PCLOS partition to grub? thanks

---

### Post by Shazaam on 2008-04-16
There are a few ways to do it. What you need to do first is find out your partition info. Run this in terminal......
```
sudo fdisk -l
```
(small L)
This code will give you a list of all of your partitions. You might want to write it down. Once you have the correct info all you would need to do then is add the PCLinuxOS partition info to fstab (if it isn't already there) and to then to grub.
To edit fstab or grub you would run this in terminal (after backing up each one).....
```
gksudo gedit /etc/fstab
```
and.....
```
gksudo gedit /boot/grub/menu.lst
```
You can also use the Ubuntu livecd to edit files on an installed os.

---

### Post by waspbr on 2008-04-17
thanks for the reply, i kinda decided to go reinstall PClo and its grub along with it, so the partition had its own menu.lst, even though it did not list ubuntu.

so I rebooted and went to konsole logged into root and did:

```
grub

root (hdx,y)

setup (hdx)
```

so I would boot again from my hardy partition, in my case my x= 0 , y = 2, I checked that in my hardy menu.lst


after that I was able to boot from hardy again, so I went into hardy and copied the relevant parts from the pclos menu.lst into hardy' s menu.lst. 

now everything works, gonna get myself a nice and cold beer to celebrate

---

