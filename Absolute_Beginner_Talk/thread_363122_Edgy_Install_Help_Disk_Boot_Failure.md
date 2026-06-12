---
title: "Edgy Install Help: Disk Boot Failure"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Zero7 on 2007-02-16
I have been reading this forum for a while. You guys are good :), but I am a noob here....

I assembled a desktop with following configuration:

Intel C2D E4300 Processor
Gigabyte GA-965G-DS3 motherboard (with onboard graphics)
1 GB RAM, (Kingston 533)
Seagate 300 GB ATA HDD

I am able to run Ubuntu 6.10 from Live CD and able to install it without any error. I have 50 GB partition for Linux. Remaining 250 GB is having lot of data and is in NTFS format.
I made 3 partitions of 8GB for /, 2 GB for swap and 40GB for home with live CD during install.  Once I complete installation, after reboot, I get a error like "Boot disk failure. Insert boot disk and hit enter"

My boot sequence is HDD and CD/DVD Rom. 

I tried manual partition option as well as automatic partition option to use the available 50GB HD space. Appreciate all suggestion and guidance.

---

### Post by nudnik on 2007-02-16
> **Zero7 said:**
> I have been reading this forum for a while. You guys are good :), but I am a noob here....

I assembled a desktop with following configuration:

Intel C2D E4300 Processor
Gigabyte GA-965G-DS3 motherboard (with onboard graphics)
1 GB RAM, (Kingston 533)
Seagate 300 GB ATA HDD

I am able to run Ubuntu 6.10 from Live CD and able to install it without any error. I have 50 GB partition for Linux. Remaining 250 GB is having lot of data and is in NTFS format.
I made 3 partitions of 8GB for /, 2 GB for swap and 40GB for home with live CD during install.  Once I complete installation, after reboot, I get a error like "Boot disk failure. Insert boot disk and hit enter"

My boot sequence is HDD and CD/DVD Rom. 

I tried manual partition option as well as automatic partition option to use the available 50GB HD space. Appreciate all suggestion and guidance.


Try reinstalling GRUB one way or another. I always use an Alternate Install CD, so that things of this type are easier. Havent used the Live CD in some time as it was plagued by bugs at one time, and not as flexible, so I cannot recall how to access this feature at the moment. 

If you have access to an Alternate CD, boot from the optical drive and enter "rescue mode". Identify your root partition and reintstall the GRUB bootloader to the master boot record.

---

### Post by Zero7 on 2007-02-16
> **nudnik said:**
> Try reinstalling GRUB one way or another. I always use an Alternate Install CD, so that things of this type are easier. Havent used the Live CD in some time as it was plagued by bugs at one time, and not as flexible, so I cannot recall how to access this feature at the moment. 

If you have access to an Alternate CD, boot from the optical drive and enter "rescue mode". Identify your root partition and reintstall the GRUB bootloader to the master boot record.

Thanks for your suggestion. Evrything is greek and latin to me:(  I do not have an Alternate CD. Could you please give me a detailed answer. I have played only with Windows so far..Win 95,98, 2K, XP.

---

### Post by nudnik on 2007-02-16
Wish I could be of more help, but I havent used the Live CD in so long I've forgotten how to access the option you need. I am positive however that someone familiar with that version can help, and I am sure there are several of them lurking about.

---

### Post by Duck2006 on 2007-02-16
[http://www.shahidhussain.com/wordpress/index.php?p=33](http://www.shahidhussain.com/wordpress/index.php?p=33)

---

### Post by Zero7 on 2007-02-16
> **Duck2006 said:**
> [http://www.shahidhussain.com/wordpress/index.php?p=33](http://www.shahidhussain.com/wordpress/index.php?p=33)

Thanks Duck! Will try tonite.

---

