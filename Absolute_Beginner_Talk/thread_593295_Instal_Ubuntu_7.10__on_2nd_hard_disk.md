---
title: "Instal Ubuntu 7.10  on 2nd hard disk"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by firdosh on 2007-10-27
i have 2 hard disk 1st 40 gb with win98 and win xp prof dual boot, i am new to Linux and have acopy of live dvd of ubuntu 7.10.
i would like to install it in 2nd hard disk i will do so after disconnecting my 1 st disk .as i am scared to disrupt my original setup.

will this work? every time i will have to change boot sequence>? or after connecting both hard disk , can i do something with external multi booter? or just to boot into linux i change boot seq in BIOS

pls help iam total beginer

firdosh

---

### Post by toddward on 2007-10-27
Welcome to Ubuntu!!

Generally, I've never had an issue where Ubuntu corrupts another install on any of my many systems.  It's very straight forward and will not install anything until it's confirmed where you're going to install stuff.  However, if you feel safer, you can always disconnect your windows disk.  One thing to consider, though, is that Ubuntu will automatically write a bootloader that will point to the various partitions.  So if you leave your disk disconnected, ubuntu will not have the requisite knowledge to write that grub.conf file.

Regarding changing which drive boots, you should only have to tell your BIOS which drive boots first, once.  When Ubuntu puts the grub.conf file in your MBR, you'll want to make sure that you try booting this drive first. 

In order to get grub.conf to point to the correct partitions, you'll want to read up on the grub boot loader.  It should tell you more information.

I hope I helped some.  It's late and I'm tired.  Please reply to this thread if you need additional help.

---

### Post by cotcot on 2007-10-27
Be carefull during installation when you come to the stage of partitioning.
Read what the partitioner wants to do. Make sure that it does not format your w98 and XP partitions. If your second hdd is empty it will automatically choose this one to make the partition(s) for ubuntu. If the second one is also full then it will shorten existing partitions.

If you are sure that your exisiting partitions are not reformatted and you have problems after reboot, do not panic. The XP bootloader can be restored easily (fix /mbr). 

Optional :
For a new installation I make a root (/) and home (/) manually using the Gparted LiveCD and do the installation of ubuntu with manual selecting these partitions in the partitioning stage.
The separate /home partition allows me to install a new ubuntu version without deleting my /home files (for instance in a case where the normal upgrade did not work)

---

### Post by firdosh on 2007-10-29
> **toddward said:**
> Welcome to Ubuntu!!

Generally, I've never had an issue where Ubuntu corrupts another install on any of my many systems.  It's very straight forward and will not install anything until it's confirmed where you're going to install stuff.  However, if you feel safer, you can always disconnect your windows disk.  One thing to consider, though, is that Ubuntu will automatically write a bootloader that will point to the various partitions.  So if you leave your disk disconnected, ubuntu will not have the requisite knowledge to write that grub.conf file.

Regarding changing which drive boots, you should only have to tell your BIOS which drive boots first, once.  When Ubuntu puts the grub.conf file in your MBR, you'll want to make sure that you try booting this drive first. 

In order to get grub.conf to point to the correct partitions, you'll want to read up on the grub boot loader.  It should tell you more information.

I hope I helped some.  It's late and I'm tired.  Please reply to this thread if you need additional help.
thanks todd, i am still skeptical abt about leting Ubutu write grub to my 1st disk mbr,  because even if i fix mbr later i might loose win98 .
can i make a complete new install in the 2nd hdd with gusty and then connect this 2nd hdd as slave and use ubutu via bios option till i am totally confident?

as i am a total novice to grub loader config file.

---

### Post by firdosh on 2007-10-29
> **cotcot said:**
> Be carefull during installation when you come to the stage of partitioning.
Read what the partitioner wants to do. Make sure that it does not format your w98 and XP partitions. If your second hdd is empty it will automatically choose this one to make the partition(s) for ubuntu. If the second one is also full then it will shorten existing partitions.

If you are sure that your exisiting partitions are not reformatted and you have problems after reboot, do not panic. The XP bootloader can be restored easily (fix /mbr). 

Optional :
For a new installation I make a root (/) and home (/) manually using the Gparted LiveCD and do the installation of ubuntu with manual selecting these partitions in the partitioning stage.
The separate /home partition allows me to install a new ubuntu version without deleting my /home files (for instance in a case where the normal upgrade did not work)
tks cot i think i will take yr advise and make a new installation on my 2nd hdd , with manual partitions and then connect this drive as slave to my 1st hdd and whenever using ubuntu i will change boot seq?  should work? mean while i will do a indept study on grub loader, any tips or sites where i can download some info

---

