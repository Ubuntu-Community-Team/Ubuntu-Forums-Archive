---
title: "No dual-boot option! Cannot auto partition HD! Gutsy 7.10 Live CD, XP"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by peterkeyani on 2008-03-13
Hello

I am trying to install ubuntu 7.10 on a freshly installed XP OS from a live CD. I have an amd64 dual core PC.

I have read the tutorials and I know I'm supposed to get a option which allows ubuntu to automatically resize and partition the HD.

I did not get this. I only got the options to install ubuntu to the whole HD or do a manual partition.

I tried this several times but I never got the auto option.

I know it can work because I've done it before. I've just had to reformat my dual boot ubuntu 7.10 XP system due to a problem in - you guessed it - the windows partition.

Thanks for your help:confused:

Pete

---

### Post by peterkeyani on 2008-03-13
> **peterkeyani said:**
> Hello

I am trying to install ubuntu 7.10 on a freshly installed XP OS from a live CD. I have an amd64 dual core PC.

I have read the tutorials and I know I'm supposed to get a option which allows ubuntu to automatically resize and partition the HD.

I did not get this. I only got the options to install ubuntu to the whole HD or do a manual partition.

I tried this several times but I never got the auto option.

I know it can work because I've done it before. I've just had to reformat my dual boot ubuntu 7.10 XP system due to a problem in - you guessed it - the windows partition.

Thanks for your help:confused:
Pete

Additional: This is what I see;

PARTITION DISC SPACE

1. Guided - use entire disk
    SCSI1 (0,0,0)(sda) - 200.0 GB ATA SAMSUNG HD200HJ
2. Guided - use largest continous space
3. Manual

Thanks for your help:confused:

---

### Post by Sbarton on 2008-03-13
You can choose 'Manual' and then create the partitions/s you need. 
Another way is to use GParted liveCD to partion your HD and then install 
Ubuntu into the Primary drive, you might also consider creating a separate
'Home' partition and 'swap' As you may know 'Grub' bootloader will overwrite XP bootloader.
regards

---

### Post by peterkeyani on 2008-03-13
> **Sbarton said:**
> You can choose 'Manual' and then create the partitions/s you need. 
Another way is to use GParted liveCD to partion your HD and then install 
Ubuntu into the Primary drive, you might also consider creating a separate
'Home' partition and 'swap' As you may know 'Grub' bootloader will overwrite XP bootloader.
regards


Thanks but I dont know how to do that.
Any idea why the auto partitioner is not kicking in or how I might activate it?

Pete

---

### Post by peterkeyani on 2008-03-13
Any ideas?
I've looked at several tutorials including screenshots but the screens and options I get are different from the tutorials - I assume because they are not talking about version 7.10 - so for someone who knows nothing about partitioning its quite impossible to dual install without the automatic partitioner which as I said doesnt appear as an option.:confused:

---

### Post by peterkeyani on 2008-03-13
> **Sbarton said:**
> You can choose 'Manual' and then create the partitions/s you need. 
Another way is to use GParted liveCD to partion your HD and then install 
Ubuntu into the Primary drive, you might also consider creating a separate
'Home' partition and 'swap' As you may know 'Grub' bootloader will overwrite XP bootloader.
regards

I have a 200 GB HD with a fresh install of windows XP on it it. It would be fantastic if you could tell me [**B]precisely what to type** including numbers[/B] in order to get ubuntu 7.10 dual installed on it. Please bear in mind that different versions of ubuntu seem to have different options and screenshots so its very confusing for a new user - Thanks!

---

### Post by Therion on 2008-03-13
I think you're a little confused here.  There is no "auto partitioner", you have to tell the installer how you want you drive partitioned as part of the install process.  You're at this stage and the installer is giving you three options:> PARTITION DISC SPACE

1. Guided - use entire disk
SCSI1 (0,0,0)(sda) - 200.0 GB ATA SAMSUNG HD200HJ
2. Guided - use largest continous space
3. Manual
1.  "Do you want to use the entire hard drive for Ubuntu?"  Most likely not, since this would overwrite your Windows install.
2.  "Do you want me to walk you through partitioning/installing but only use the biggest chunk of free space available on your hard drive?"  This may be what you want since your Windows install is NOT "continuous space".
3.  "Do you want to set up your partitions all by yourself?"  Judging by your post, I would say not.  

What I suggest you do is download the [gParted LiveCD](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828).  This will give you an easier-to-use/understand-what-you're-doing graphical interface *and* allow you to shrink your Windows partition (defragging is a good idea prior to this step) before using the Ubuntu install CD.  Then you have a partition all ready to go for Ubuntu to install itself on.

---

### Post by Therion on 2008-03-13
I think you're a little confused here.  There is no "auto partitioner", you have to tell the installer how you want your drive partitioned as part of the install process.  You're at this stage and the installer is giving you three options:> PARTITION DISC SPACE

1. Guided - use entire disk
SCSI1 (0,0,0)(sda) - 200.0 GB ATA SAMSUNG HD200HJ
2. Guided - use largest continous space
3. Manual
1.  "Do you want to use the entire hard drive for Ubuntu?"  Most likely not, since this would overwrite your Windows install.
2.  "Do you want me to walk you through partitioning/installing but only use the biggest chunk of free space available on your hard drive?"  This may be what you want since your Windows install is NOT "continuous space".
3.  "Do you want to set up your partitions all by yourself?"  Judging by your post, I would say not.  

What I suggest you do is download the [gParted LiveCD](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828).  This will give you an easier-to-use/understand what you're doing graphical interface *and* allow you to shrink your Windows partition (defragging is a good idea prior to this step) before using the Ubuntu install CD.  Then you have a partition all ready to go for Ubuntu to install itself on.

---

### Post by konungursvia on 2008-03-13
I agree with Theron, and I think what you are looking for is option 3. You can also resize them later on. Make sure you defragment the windows drive several times in Windows itself before doing install.

---

### Post by Sbarton on 2008-03-13
peterkeyani, Gparted Live CD seems to be the way for you, to partition your HDD. As has been suggested 'Defrag' windows first then partition.
The following is a guide to GParted, it does not include dual boot but can familiarise you with Gparted  [http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

Take time with Gparted, you are given opportunities to go back on your choices before commiting any action, but it works very well.

I would say that if you had another HDD you could use as a slave drive I would go that way which is easier as no XP is involved on that drive. If not go with Gparted Live CD and take your time.
Good luck!
regards

---

### Post by peterkeyani on 2008-03-18
> **Sbarton said:**
> peterkeyani, Gparted Live CD seems to be the way for you, to partition your HDD. As has been suggested 'Defrag' windows first then partition.
The following is a guide to GParted, it does not include dual boot but can familiarise you with Gparted  [http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

Take time with Gparted, you are given opportunities to go back on your choices before commiting any action, but it works very well.

I would say that if you had another HDD you could use as a slave drive I would go that way which is easier as no XP is involved on that drive. If not go with Gparted Live CD and take your time.
Good luck!
regards

I think I figured it out. I ran "Dariks Boot and Nuke" on the HD first and reinstalled XP. This time ubuntu 7.1 gave me the option of automatically resizing the partitions and installed ubuntu on the other partition for me. I guess the lesson is the HD must be completely clean, free of errors and defragged for the auto resize option to work.

Thanks all.

pete

---

### Post by Sbarton on 2008-03-19
> **peterkeyani said:**
> I think I figured it out. I ran "Dariks Boot and Nuke" on the HD first and reinstalled XP. This time ubuntu 7.1 gave me the option of automatically resizing the partitions and installed ubuntu on the other partition for me. I guess the lesson is the HD must be completely clean, free of errors and defragged for the auto resize option to work.

Thanks all.

pete

Thanks for your feedback and glad you got it sorted!
Maybe you can mark the post as SOLVED so others may find it helpful.
regards

---

