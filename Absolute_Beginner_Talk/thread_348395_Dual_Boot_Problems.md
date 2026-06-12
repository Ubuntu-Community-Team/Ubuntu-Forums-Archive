---
title: "Dual Boot Problems"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Xendoncehat on 2007-01-28
Hello

I've been trying to install a dual boot setup on my laptop and so far I haven't succeeded in it. I've read through loads of sites with instructions, tried to do as they tell but no dice.
Every time I try to to boot to windows I get a dual screen saying something (don't remember). It always happens when windows starts to load itself.
I have ubuntu-6.06.1-desktop-i386-fi.iso (finnish version) and the laptop is an IBM thinkpad T41 if that matters.

If someone would be willing to tell me how to setup a _working_ dual boot setup step by step, I would be a happy man. 

But now I have some biology to study.

Cheers.

---

### Post by old_geekster on 2007-01-28
It is btter to install Windows first.  Make the partition at least half of the drive, leaving the remainder as "Free Space".  This makes it better for Ubuntu.  

I have just recently installed Ubuntu Edgy Eft 6.10 about 6 times, because I mess things up experimenting.  I have it on my second HDD, so I really don't have a true dual-boot situation.  At least, both OS'es aren't on the same drive.  However, I have done a dual-boot with Windows and SuSE 10 on the same drive.

Once you have installed Windows, then you can begin the install of Ubuntu.  Ubuntu will recognize that Windows is on the drive and add it to GRUB [COLOR="black"](_GR_and _U_niversal _B_ootloader)[/COLOR].  It will partition the remainder of your drive for you or you can choose "Manual Partition".  Once the partitions are established, the OS will begin to install.

During boot, GRUB will appear and give you the choice of OS'es.  You can use the arrow keys to move around in GRUB.

This may seem like a streamlined version, but this is actually how easy it is to setup.  The partitioning is the most difficult part.  As I stated, Ubuntu will do that for you, if you desire.  Simply take your time and read all of the prompts carefully.  You can do it!

---

### Post by m_p_m on 2007-01-28
A good resource is at [http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html) 

I have used this in the past to boot up linux from the windows boot loader (in winXP). Comes in handy if things go wrong with the boot loader as it is easy to use the windows install disk to restore the MBR

---

### Post by Xendoncehat on 2007-01-29
Ok, so this is what I'm trying to do

[http://img222.imageshack.us/img222/8121/kuvakaappaustv3.png]("http://img222.imageshack.us/img222/8121/kuvakaappaustv3.png")

Since I'm installing dapper drake it doesn't have that nifty slider in the installing options. Only manual partitioning, use biggest space (or something) and format disk.

Should it work like that? And what about these mounting points. I'm a bit lost here.

Edit: I tried some guides on the net and I still got the same result. When I select Win XP in GRUB, Windows starts to load and after about one second I get a bluescreen saing "unmountable_boot_volume" to me. Then the computer restarts.

---

### Post by housam on 2007-01-29
I've posted this before, read it . it may help you.> About partitioning , You only able to create 4 primary partitions on a single HDD. If you need more partitions , you have to convert one of the primary partitions to an extended partition which can be devided to any number of partitions you want.
Please note that partition magic is not the suitable tool for partitioning for ubuntu. use the Gparted to do the job, it is perfect for ntfs and ext3 format.
Do the defrag at least twice before resizing your xp partition and back-up every thing. create all your partitions manually before installing ubuntu, that put every thing under control. here is an example:
Resize the windows poartition to create an unallocated space of about 41Gb ( or what ever you like )
Now devide the unallocated space to two new partitions:
-10 Gb ext3 for the root ( / ) as primary partition
-31 Gb as EXTENDED PARTITION
Devide the extended partition to 2 new logical partitions
-1 Gb swap for the ( swap )
-30 Gb ext3 partition as /home 
After that go for the installation and when it comes to the partition mater , choose the manual way .

---

