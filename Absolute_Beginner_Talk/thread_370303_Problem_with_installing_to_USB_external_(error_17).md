---
title: "Problem with installing to USB external (error 17)"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by chieferer on 2007-02-25
hi, here is my situation; i have a 60 gig internal HDD which has an XP installation on it and is almost full.  Now i wanted to try Ubuntu but i have no space on my internal HDD.  I do, however, have a 100 gig USB external HDD which is less than 50% full.  i partitioned my external so that there is a 15 gig ext3 partition for the / directory.  i also added a 1.3 gig swap partition.  everything went well in the install but when i tried to boot up, i got error 17: unable to mount selected partition.  i did select to install grub to (hd1) when i was given the option.  i do not know what to do.  any ideas? (BTW i need to keep my XP installation so please don't suggest a fresh install).

---

### Post by cappa72 on 2007-02-26
Hi,
There is one question concerning the partition of your external (usb) hdd: was it partitioned as primary or logical partition?

If you install the grub to hd0, then you will have the chance to boot.
Be careful! Prior to do anything, make a boot disk for xp. If your grub install is failed, you can boot from win boot floppy and the 'fdisk /mbr' will recover your internal hdd&#8217;s master boot record and the xp will boot again as default.

If this way doe not work, I have got some other ideas.

---

### Post by chieferer on 2007-02-26
i believe i made primary partitions

---

### Post by dannyboy79 on 2007-02-26
if you installed grub onto hd1, and you only have 1 internal hard drive and then the other hard drtive is external, than i am guessing you installed grub onto your external hard drive. there are several ways to fix this, if you're motherboard is capable of booting to an external usb device, than just chnage your bios so that it boots your external drive first and that should booot up grub since you installed grub onto your mbr of that drive. if your motherboard can't do that, then you'll have to install grub onto your winxp hard drive which will install grub onto the mbr of that drive. don't worry it won't mess up your install. if you're going with option 2 than you can just use a live cd to install grub onto your winxp drive but it's a hell of a lot easier to use the super grub disk! you can download it here, [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)
 there are also instructions there as well. i can't really explain how to do it because I am at work and it would take me awhile to help you, I would suggest reading the website that I have linked to here or look thru this forum for grub error 17 threads, and they will already be solutions written up on those threads. good luck

---

### Post by chieferer on 2007-02-26
thanks.  my bios is set to boot from internal HD fisrt.  
(sorry just clarifying) i gather from your post that if i set it to boot from an external USB drive the problem would be solved. am i right?

---

### Post by dannyboy79 on 2007-02-26
yes, that is if all other criteria are met with my example. you had only 1 internal hard drive when you performed the install. you had only 1 external usb hooked up drive whne you did the install. you chose hd1, which since you only had 1 internal drive (winxp) that would have been hd0 to grub, so that means that you installed grub onto the mbr of your ecternal disk. if your computer can boot to a usb device you should be ok BUT, there may be additional steps you need to take to be able to boot to a usb device. you need to search within this forum, I know it has been done. also, once you get your system booting to your external usb, that doesn't mean that winxp will automatically show up within your grub menu, you may need to add it. again, you'll have to search the forums as I am work and can't help more than what I am. good luck.

---

