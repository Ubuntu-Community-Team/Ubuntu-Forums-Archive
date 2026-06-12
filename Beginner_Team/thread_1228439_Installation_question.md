---
title: "Installation question"
date: 2009-07-31
forum: Beginner Team
---

### Post by Cortux on 2009-07-31
I would soon have no need for Vista on my machine. I currently have a dual boot option with Ubuntu 9.04 with Vista business.
 
Would I be able to remove Vista safetly and allow Linux to take the rest of the space or do I have to do a new installation because of the partitioning issue. I would like to keep my configuration and already installed programs. Is this possible.
 
Thanks

---

### Post by x33a on 2009-08-01
yes, you should be able to remove vista without a problem (assuming you are using grub).

---

### Post by Cortux on 2009-08-01
Sorry, im a newbie. Can you explain what is, how to install and how to use grub to uninstall the vista os.

---

### Post by x33a on 2009-08-01
boot into ubuntu. 

open gparted:

system -> administration -> partition editor

1. choose the vista partition.

2. delete that partition and format it to ext3.

you are done.

and after that you'll have to remove vista entries from /boot/grub/menu.lst

by the way, grub is the bootloader of ubuntu. it lets you choose which os to boot into.

---

### Post by Cortux on 2009-08-03
Excellent, Thank you.
 
I would assume that once thats done, the original Ubuntu install will be combined with the space formatted.

---

### Post by Cortux on 2009-08-08
I have decided to install xp over vista instead of uninstalling vista completely for now. 
Is this possible without effecting the Linux partition. ?????

How could I go about this???

Thanks

---

### Post by x33a on 2009-08-08
well you can install xp on vista's partition, but then windows bootloader will overwrite grub, and you'll have to restore grub.

download and burn supergrubdisk, and use it to restore ubuntu's bootloader later on.

[http://supergrubdisk.org/](http://supergrubdisk.org/)

---

### Post by Cortux on 2009-08-09
> **x33a said:**
> well you can install vista on xp's partition, but then windows bootloader will overwrite grub, and you'll have to restore grub.

download and burn supergrubdisk, and use it to restore ubuntu's bootloader later on.

[http://supergrubdisk.org/](http://supergrubdisk.org/)

Hi, its gonna be XP sp3 over vista's partition, should I just boot from the XP disk and follow the usual installation procedure, is there any risk of writing over Linux with the exception of Ubuntu's bootloader you mentioned.

I checked the link, not sure which one to download and how to use it, can you advise me further.

Just one more thing, To be safe I would like to make a full backup of everything Ubuntu including the installed programs, configuration, settings etc. I hear its possible but im not too sure on how to do this and how to apply back to the Notebook when required.

Thanks Again.

---

### Post by x33a on 2009-08-09
firstly, sorry for the xp/vista confusion :D

as for installing xp over vista, you can use the xp disc to delete vista's partition and install xp over that space.

after that you'll have to recover grub (using supergrubdisc)

download supergrubdisk iso from here:

[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso)

and burn it to a cd.

as for system backup, well i've never done a full system backup myself (i just burn my data to a data dvd), but these links will help you out.

[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Cortux on 2009-08-10
> **x33a said:**
> firstly, sorry for the xp/vista confusion :D
 
as for installing xp over vista, you can use the xp disc to delete vista's partition and install xp over that space.
 
after that you'll have to recover grub (using supergrubdisc)
 
download supergrubdisk iso from here:
 
[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso)
 
and burn it to a cd.
 
as for system backup, well i've never done a full system backup myself (i just burn my data to a data dvd), but these links will help you out.
 
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)
 
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
 
Cool, No need to apologise, you have been extremely helpful so far.
 
I will get going as soon as I reach home tonight and keep you posted.

---

### Post by Cortux on 2009-08-10
So Far, I downloaded the Supergrub image succesfully, it does boot up with supergrub because the interface is different from original boot screen.
 
If grub is erased, does supergrub reinstall automatically ???

---

### Post by x33a on 2009-08-11
you'll have to select the option from the live cd to restore grub.

---

### Post by Cortux on 2009-08-11
I have not seen the option when testing the disc to see if it boots, is it in the main menu or should I navigate to the option ?

---

### Post by x33a on 2009-08-11
maybe this could help:

[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

---

### Post by Cortux on 2009-08-12
OK, I just installed XP, booted with xp disc, reformatted NTFS partition, took some time to load xp drivers from dell website, thereafter rebooted with Supergrub disk and just loaded the auto option. Work perfectly after that, I just need to find the xp fingerprint driver, but I will call dell today for that one.
 
Thanks, you have been a great help.
 
One other thing however not very serious is in the boot screen, there are so many Ubuntu's to select from and the name Vista is still there, when I select Vista, it gives an option of two XP selections. Is there a way to remove those and just have the Ubuntu, Ubuntu Recovery and XP options to choose from when booting.

---

### Post by x33a on 2009-08-12
could you post the output of
```
cat /boot/grub/menu.lst
```

and from windows C: the contents of boot.ini

---

### Post by Cortux on 2009-08-13
Ok. I have recieved some help from one of the guys at work, its now sorted out. He used the same command which you posted for me to use. I wish I knew what you guys know (hardcore stuff).

Thanks, I have to start learning more. Its way too much fun.

---

