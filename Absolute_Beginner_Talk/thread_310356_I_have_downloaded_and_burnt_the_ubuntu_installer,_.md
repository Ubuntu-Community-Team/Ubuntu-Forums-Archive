---
title: "I have downloaded and burnt the ubuntu installer, now what?"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2006-12-01
After downloading and burning ubuntu 6.10, I tried running the program and windows can't run it. I tried to boot my laptop with the cd and nothing still happened. The installer doesn't seem to be bootable or something. Can somebody help me with this? I'm an absolutely innocent newbie :D

---

### Post by Scorpuk on 2006-12-01
You need to go into your computers bios and tell it the first boot device is your CD.


Be careful what you do in the bios as this is the information the computer needs to start and if you change something by mistake then it may not work again. :mrgreen:

---

### Post by 23meg on 2006-12-01
Are you sure you burned a bootable CD?

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by sand4us on 2006-12-01
Ubuntu/linux is an OS, are you trying to replace winxp with this?  If not I wouldn't booting to it!  If you want to run linux you'll either need to have another box(PC) or dual boot your system.  Just my thoughts!:twisted:

---

### Post by wersdaluv on 2006-12-01
ok... This is what I actually want to do...

I want to try this dual booting thing so that I can keep XP. Do I download this grub thing?

---

### Post by wersdaluv on 2006-12-01
> **23meg said:**
> Are you sure you burned a bootable CD?

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)


I assumed that after burning the ubuntu installer, it's going to be bootable. Isn't it that way? How do I know if it's bootable?

---

### Post by CatKiller on 2006-12-01
> **wersdaluv said:**
> How do I know if it's bootable?

When you browse the cd in Windows, if there's only one file, then you've done it wrong.

---

### Post by wersdaluv on 2006-12-01
ooohh.. I've burnt only one file. 

When I downloaded ubuntu, I got an iso file and an iso.part file. I wasn't able to burn the iso.part file because, the iso file is almost 700mb and the iso.part file wont fit anymore. 

What should I do?

---

### Post by CatKiller on 2006-12-01
> **wersdaluv said:**
> ooohh.. I've burnt only one file. 

When I downloaded ubuntu, I got an iso file and an iso.part file. I wasn't able to burn the iso.part file because, the iso file is almost 700mb and the iso.part file wont fit anymore. 

What should I do?

The tutorial linked to above suggests **CDBurnerXP** to burn the ISO image **as an image**. It will be the .iso file you're interested in - the .part file should just be a temporary file.

---

### Post by wersdaluv on 2006-12-01
Thank you so much! I'm starting to see where it went wrong. :)

---

### Post by antharr on 2006-12-01
You have to burn the iso as an image. What kind of burning software are you using? :-k 
 
After correctly burning the image you can actually run Ubuntu because it is a Live CD. .You can play around with it to see if it is to your liking.If you like what you see and you do want to dual-boot, you will have to partition your HDD so that your computer will dual-boot. 

Something like this is an example. 
Say you have an 80 Gig HDD. 

Windows XP with a NTFS file system----->20 Gigs
Shared partition with a Fat32 file system------->20 Gigs
Linux partition with a ext2 file system--------->39 Gigs
Swap partition----->1 Gig



This is just an example and you can take the extra storage space from one and add to the other except the swap. The swap should be 2X the memory installed on your on your computer. Also the shared partition is not necessary. I like having a shared Fat32 to make it easy to share files between Windows and Linux.If you like what you see on the CD then the above can be explained in numerous postings and tutorials on the site, or I am sure someone would be glad to help out if you need a little more insite.

---

