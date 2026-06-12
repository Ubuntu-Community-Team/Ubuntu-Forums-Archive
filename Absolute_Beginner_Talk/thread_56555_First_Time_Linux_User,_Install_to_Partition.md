---
title: "First Time Linux User, Install to Partition?"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by decile on 2005-08-13
Alright I got one of the Ubuntu CDs in the mail and I would like to install it to a partition I already have setup. I am as new as new can get in the Linux world and the wiki isnt specific enough for me. When I boot from the CD I press F1 and I've been trying to find how to install to a partition or create a new one but was unsuccessful.

So how do I install Ubuntu to a partition, I guess I need step by step instructions? 

Thanks guys.


EDIT: Ok I am at the partition screen and I have chosen the partition I would like to use. I am stuck at Use Partition As:

---

### Post by PeP on 2005-08-13
split your partition in two.
one big
one just the half of your ram (~200 mb is ok)
use the first one as root (   /    )
and choose an ext3 fs
the second one as swap.

if you have mor than ten Gigs split in three and use the same swap,  5~7 gigs for root and anything else as home ( /home )

---

### Post by gord on 2005-08-13
i was a little bit confused by the partitioning myself at first but i have a few tips.

first off i found it best to do a manual partition, might not work very nicely for you though. so select that one from the list.

you should also first decide how you want your setup to work. you can keep windows and linux compleatly seperate and have just two partitions (one for windows and one for linux) but it helps to have a space that both windows and linux can use.

so you should generally split your drive up into three partitions, one for windows (ntfs) one for linux (ext3) and one for both (fat32).

you are prolly going to want to run windows as well yes? well i'll asume you do. so you will want to **resize** your windows partition that you allready have (make it smaller). 
you should then end up with two parts to your drive, a partition for windows and a load of free space.

you can then get creating new partions for linux and fat32. its upto you how you size this. just make sure they are big enough. 

when the linux partition is made it should also create a smaller 'swap' partition for you.

i can't quite remeber the in's and outs but thats the general jist of the thing :)

---

### Post by Digitallysick on 2005-08-13
you might want to try partition magic , in windows, for me its the easiest to deal with. i had to reformat my hd so many times due to screwing up linux installs when i first tried on my 300 mhz packedbell (i dont think linux was supported by any of that hardware at the time) didn't stop me from trying, it has came along way!

---

### Post by nic2 on 2005-08-13
[QUOTE=decile]Alright I got one of the Ubuntu CDs in the mail and I would like to install it to a partition I already have setup. I am as new as new can get in the Linux world and the wiki isnt specific enough for me. When I boot from the CD I press F1 and I've been trying to find how to install to a partition or create a new one but was unsuccessful.

So how do I install Ubuntu to a partition, I guess I need step by step instructions? 

Thanks guys.


EDIT: Ok I am at the partition screen and I have chosen the partition I would like to use. I am stuck at Use Partition As:[/QUOTE]
I have found that by deleting the partition you want to use for Ubuntu (using the installer) and thereby creating free space, one is able to install Ubuntu to the free space using the automatic partitioning option.

---

### Post by TristanMike on 2005-08-14
[QUOTE=nic2]I have found that by deleting the partition you want to use for Ubuntu (using the installer) and thereby creating free space, one is able to install Ubuntu to the free space using the automatic partitioning option.[/QUOTE]I'm uber-new too, and although the install confused me too, this method I found was best untill I learn the in's and out's of Linux/Ubuntu. Once I had the selected space set aside for Linux/Ubuntu I just let it automatically partition it for me, just like the gentleman above, and worked like a charm.

I also have the FAT32 drive as suggested and I too suggest it. If I had set it up without it, I would be kicking myself in the pootkas for sure.

I hope you have fun, I sure as heck have been.

---

### Post by redfox on 2005-08-15
Knoppix is a great way to partition a HD as well.  The newer versions (3.9, 4.0, and maybe older) have a nifty utility called QTparted, iirc.  It's free and partions quite well.

My question (as I prepare to install tomorrow) is: do I need to create the swap partition beforehand, or can I do this in the install?

---

### Post by TristanMike on 2005-08-15
[QUOTE=redfox]My question (as I prepare to install tomorrow) is: do I need to create the swap partition beforehand, or can I do this in the install?[/QUOTE]
If I remember correctly the installer should create it on it's own if, when in the manual partition section, you allow the installer to Automatically Create Partions or something very similar. You will see it create the main ext3 filesystem, and a swap partition (which you can edit if you like).

---

