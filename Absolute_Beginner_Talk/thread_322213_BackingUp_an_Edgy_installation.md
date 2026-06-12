---
title: "BackingUp an Edgy installation"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by scweston on 2006-12-20
I presently have a fully working installation of Edgy running from an external USB harddrive on my laptop. 

My current hardware configuration is:
Laptop with 80Gb hdd - windows XP installed (ntfs)
30Gb USB hdd - partitioned with ext3 (18gb) root; fat32 (10Gb) for saving things; swap (2gb)
250Gb USB hdd - single partition (ntfs), which I use for backing-up on to.

I wish to make modifcations to my edgy installation to install the ATI drivers that will allow me to use software such as Google Earth. I've tried this before and completely messed things up (thing wouldn't boot properly and i was too out of my depth to be able to fix things), so this time I want to be able to recover using a backup.

I usually use Norton Ghost to back up my Windows installations... could I boot in to windows to use this software to back up an ext3 drive. Also do I need to back up the swap partition too?

Or is there other software that will be better, that I could use from within linux, to backup on to my 250Gb USB drive.

Also, after restoring the ext3 partition, will I need to reinstall grub? Presently grub is installed on the 30Gb usb drive and the computer boots directly from the USB drive?

Thanks for your help.
Stephen

---

### Post by xyz on 2006-12-20
Hi,
Many ways to back up. Here is one of them:
[Using PartImage in Ubuntu]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by eppoh on 2006-12-20
I used Acronis true image. It supports Linux and will mirror your entire drive, even if you dual  boot with just a couple moust clicks. 

It is a bit pricey, but saved my bacon when my drive crashed. I was up and running in the time it took to physically swap em out.

---

### Post by whoismilan on 2006-12-20
I just use tar: [http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

Simple, fast, you can back-up/restore when logged in, choose what to back-up/not back-up, you already have the program required to do this installed on Ubuntu (and on all other Linux distributions as well), and so on...

---

