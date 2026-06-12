---
title: "ASUS G75V not able to boot up with GRUB"
date: 2012-09-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Pioter11 on 2012-09-14
My laptop - ASUS G75V no blueray
Ubuntu version 12.04
Native OS:Windows 7 Home Premium
 
So I tried 3 things:
Live DVD install - When I booted with UEFI, the screen had all messed up colors, and I was not able to do anything. So I choose the other option. Then I got into the main installer screen. I tried running the installer, no go. I had to run the installer with the option of nomodeset to get it to install. To verify installation I went on the try ubuntu without installing, and I saw the folder setup. I also ran the disk consistency check, wwhich succeed. But I was not able to run Ubuntu because GRUB was not popping up.
My boot sequence is Windows Boot Manager first then dvd.
 
I tried going to the try ubuntu a second time, at which point i did the following commands:
 
sudo fdisk -l
sudo mount /dev/sd4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
sudo update-grub
 
All commands succeeded but the last. And still no grub on restart.
 
Secon attempt: Wubi off of windows 7 home premium. I ran the wubi installer, on a formatted drive. It installed, this time again no grub, BUT in the windows boot manager there is a ubuntu option. Which when clicked, errors out with the following message:
\ubuntu\winboot\wubildr.mbr 
does not exist or is corrupted.
 
Third attempt run wubi off of usb key. Same as above.
 
 
HELP ME! Please
 
Let me know any specs or anything else to provide to help in resolution.

---

### Post by BrianBlaze on 2012-09-14
First off I am very jealous of your laptop... it puts my G53SV to shame :) Second I am wondering if you installed grub on your Ubuntu partition. It sounds to me like that could be the problem and maybe you skipped that step during install?

---

### Post by Pioter11 on 2012-09-14
1

---

### Post by Pioter11 on 2012-09-14
> **BrianBlaze said:**
> First off I am very jealous of your laptop... it puts my G53SV to shame :) Second I am wondering if you installed grub on your Ubuntu partition. It sounds to me like that could be the problem and maybe you skipped that step during install?
 
 
So, where would you like me to start off, option 1 or 2? I don't have a USB key available right now, Next, how can I check? And if I didn't get grub on my ubuntu partition, how could I fix it?

---

### Post by BrianBlaze on 2012-09-14
If you go through the install again right after you make your partitions and press next it asks you if and where u wanna put the grub boot loader (custom installation). Otherwise I am not really a pro when it comes to the new grub but practice makes perfect :)

---

### Post by redpiersystems on 2012-09-15
I think I may be able to offer an answer.

I have the ASUS G75VW-DS72 notebook with Ubuntu 12.04.1 ...I tried using Ubuntu 12.04, but because a lot of packages are no longer "supported", I had to use Ubuntu 12.04.1

See my HOWTO post: [http://ubuntuforums.org/showpost.php?p=12241087&postcount=1](http://ubuntuforums.org/showpost.php?p=12241087&postcount=1)

---

