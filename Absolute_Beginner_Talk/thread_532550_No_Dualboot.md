---
title: "No Dualboot"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by sniktaw on 2007-08-22
I have been a windows user for many years and have got bored with it, so i decided to give ubuntu a go as i have heard good things about it,

I downloaded the ubuntu 7.04, burned, and inserted into pc and restarted,

So went through the installation easily and set-up my hard drive as follows

Partition 1 - Windows XP - 34gb
Partition 2 - Ubuntu 7.04 - 4gb
Partition 3 - Swap - 2gb

it all went fine, finished installation and restarted PC, the pc restarted and loaded up windows straight away, so i restarted again and it still loaded up windows,

So i have been given no option of which OS i would like to load up.

I have had a look around here and as far as i can tell GRUB should av been installed and there should have been some mention of it during the Ubuntu installation but there wasnt.

I downloaded the "super grub disk" but found it abit confusing and would like some information before i go playing around with something that i know nothing about.

I really dont want to loose my windows install either...

So my question is...

How can i get the option of which operating system i want to load when i switch on my pc?How can i get the option of which operating system i want to load when i switch on my pc?

I will be grateful for any help you guys/gals can give me

Thanks
SNiKT4W

---

### Post by jdrodrig on 2007-08-22
just curious, did your windows partition in fact got reduced to 34gb?

I am just thinking maybe nothing got done...

you can try ([http://www.fs-driver.org/](http://www.fs-driver.org/)) to read the ext partition...

but in any event, lets wait for the more experienced posters to arrive..

---

### Post by sniktaw on 2007-08-23
I partitioned my harddrive during the linux install, the windows partition was 40gb so i reduced it to 34gb and created the linux and swap partitions

thanks for your reply

---

### Post by sniktaw on 2007-08-23
Could anyone tell me how to setup dual boot myself?

---

### Post by pgar23 on 2007-08-23
> **sniktaw said:**
> Could anyone tell me how to setup dual boot myself?

Check my signature...VIDEO TUTORIAL!
 |
 |
 |
 V

---

### Post by sniktaw on 2007-08-23
Great video very helpful but im afraid that it didnt help me at all :(

when i installed ubuntu it installed straight from the linux live cd desktop, and it never asked me about adding grub to the master boot record nor did i see anything about a bootable flag :confused:

Well i downloaded and burned "super grub disc" but i would just like some information on how to use it, 

Fancy making another video guys :) lol just kidding, but if you could help or anyone else i would be grateful,

does anyone think it would help if i just removed ubuntu and the last 2 partitions and started over again:confused:

I dunno...lol

Thanks

---

### Post by bren on 2007-08-23
you don't need to remove and start again.

please open a terminal window and type

sudo fdisk -l

and post back the results

then next steps are here

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation)

---

### Post by sniktaw on 2007-08-24
thanks, i will give it a try as soon as i get in tonight, thankyou

---

