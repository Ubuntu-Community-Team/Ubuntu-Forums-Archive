---
title: "Help with Partition / Grub / MBR / Ubuntu Install"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by richbarna on 2006-06-28
I want to install Dapper on a blank partition for testing Edgy without messing up my current Dapper install (I have previously borked and reinstalled). Could anyone tell me if the way I am going to do it is the best way ?

[ATTACH]11893[/ATTACH]

1. Use gparted to create an ext3 Primary Partition called Hdc4
2. Install Dapper to Hdc4 (with 512Mb Swap at the end)
3. Say "no" to MBR/GRUB install
4. Boot into present Dapper and add Hdc4 distro to MBR/GRUB.

If anyone can see a problem with this, or if somebody knows an easier way, I would be grateful.

---

### Post by klytu on 2006-06-28
I am somewhat unsure of your question. Do you have a working Dapper installation already? If so, why not put the Edgy distribution you wish to test on the blank partition? If you already have GRUB set up to boot your Dapper installation default, you could then just add a menu selection to boot the Edgy distribution you wish to test.

---

### Post by richbarna on 2006-06-28
[QUOTE=klytu]I am somewhat unsure of your question. Do you have a working Dapper installation already? If so, why not put the Edgy distribution you wish to test on the blank partition? If you already have GRUB set up to boot your Dapper installation default, you could then just add a menu selection to boot the Edgy distribution you wish to test.[/QUOTE]

That's exactly it. I'm going to install "another" Dapper to the empty partition, upgrade it to Edgy for testing and add it to the MBR/Grub of my already installed Dapper.

I just want to make sure that the method I want to use will work. I really don't want any of this to affect my present Dapper install. (I had to do a reinstall before).
I have installed and tried lots of linux distros on my "testing" laptop, but this time I have to use my desktop due to RAM etc.

---

### Post by klytu on 2006-06-28
[QUOTE=richbarna]That's exactly it. I'm going to install "another" Dapper to the empty partition, upgrade it to Edgy for testing and add it to the MBR/Grub of my already installed Dapper.

I just want to make sure that the method I want to use will work. I really don't want any of this to affect my present Dapper install. (I had to do a reinstall before).
I have installed and tried lots of linux distros on my "testing" laptop, but this time I have to use my desktop due to RAM etc.[/QUOTE]

This should work fine. I have done the same type of thing myself several times and haven't messed up my working installation (maybe I have been lucky???). But you will really be updating the menu.lst file for GRUB on your current working installation; you should not be altering your MBR. If you need help with setting up the GRUB menu, I could walk you through it. So far your partioning set-up looks fine.

---

### Post by richbarna on 2006-06-28
Thanks for the quick replies klytu,

I'm not exactly a newbie, and i have used/installed many distros, it's just that sometimes someone else nows a better way to do something so I thought i'd post and check.

Thanks for the help :)

I can "forum search" and "Google" the Grub menu part, but thanks a lot for the offer of the walk-through. Much appreciated.

---

### Post by richbarna on 2006-06-28
Now posting from my new install.
I just thought I would point out a few things in case somebody wants to do the same as I did.

Using Gparted (Gnome Partition Editor)

1. You can't have more than 4 active partitions, so in your free space you have to first change it to an "extended" partition which will then put a light blue border around it.

2. In this partition you need to create three more, and you have to do it going backwards.
(a) Swap partition 512 Gb (If you haven't got much RAM) Read up on swap
(b) Home partition ? Gb    (How ever much you've got left after swap & root)
(c) Root partition 2.5 Gb   (It says minimum 2Gb when it should say 2048Mb)

After I reinstalled and booted, to my surprise, both distros were already listed, so I didn't even have to worry about the Grub boot list.

---

### Post by user1397 on 2006-06-28
[quote=richbarna]Now posting from my new install.
I just thought I would point out a few things in case somebody wants to do the same as I did.

Using Gparted (Gnome Partition Editor)

1. You can't have more than 4 active partitions, so in your free space you have to first change it to an "extended" partition which will then put a light blue border around it.

2. In this partition you need to create three more, and you have to do it going backwards.
(a) Swap partition 512 Gb (If you haven't got much RAM) Read up on swap
(b) Home partition ? Gb    (How ever much you've got left after swap & root)
(c) Root partition 2.5 Gb   (It says minimum 2Gb when it should say 2048Mb)

After I reinstalled and booted, to my surprise, both distros were already listed, so I didn't even have to worry about the Grub boot list.[/quote]actually, you don't need to make a new swap partiton or a home partition.  A separate home partiton is only useful if you're going to reinstall your os, because you can keep all of your settings and files in an unaffected region, called /home;).  

If you already had a swap partition, then you dont need to make another one, linux distros can all share one swap partition.

Whenever I install a new os (apart from dapper), I follow the same steps as you, richbarna, but I make the new os be on one partition, /, so it's easy to keep track of, and I know that i'm not going to need a /home partition for that os because it's not my primary os, and i'll probably delete my new os sometime in the near future, to try out another one.

Other than that, you did everything right.

---

### Post by user1397 on 2006-06-28
by the way, richbarna, how much ram do you have? that swap space looks a little excessive in size!  (I have 1 GB of ram, and my swap is only 258MB!, and it still practically never gets used!)

---

### Post by richbarna on 2006-06-28
[QUOTE=erik1397]actually, you don't need to make a new swap partiton or a home partition.  A separate home partiton is only useful if you're going to reinstall your os, because you can keep all of your settings and files in an unaffected region, called /home;).  

If you already had a swap partition, then you dont need to make another one, linux distros can all share one swap partition.

Whenever I install a new os (apart from dapper), I follow the same steps as you, richbarna, but I make the new os be on one partition, /, so it's easy to keep track of, and I know that i'm not going to need a /home partition for that os because it's not my primary os, and i'll probably delete my new os sometime in the near future, to try out another one.

Other than that, you did everything right.[/QUOTE]


Damn It!! You see? that's why I posted before, nobody told me that :rolleyes: 
I should've googled some more, my fault :-\" 

The other reason I did it this way, was if all went well, I know I already have the three partitions ready just in case I decide to install a different distro in the same space. (Bit of a distro junkie)

I also thought that the information may be useful for somone else who is relatively new to partitioning and installing/dual booting.

Thanks for the swap info ;)

---

### Post by richbarna on 2006-06-28
[QUOTE=erik1397]by the way, richbarna, how much ram do you have? that swap space looks a little excessive in size!  (I have 1 GB of ram, and my swap is only 258MB!, and it still practically never gets used!)[/QUOTE]

Ah yeah, ha ha. At the moment 512 Mb (2X 256). I've currently got 5 boxes in different states of destruction (I change around a lot).

I often swap RAM, Procs, HDD's from one box to another depending on how bored I am :lol: 

This box only had 256Mb RAM when I originally installed Dapper.

---

### Post by user1397 on 2006-06-28
[quote=richbarna]Ah yeah, ha ha. At the moment 512 Mb (2X 256). I've currently got 5 boxes in different states of destruction (I change around a lot).

I often swap RAM, Procs, HDD's from one box to another depending on how bored I am :lol: 

This box only had 256Mb RAM when I originally installed Dapper.[/quote]ah, well then i guess your swap size is decent.

---

