---
title: "Reinstallation Questions"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by ucsdrake on 2007-01-22
hey,

I'm still a new user with Ubuntu and I'm just about to reinstall it as my first install had a problem i found quite annoying, any help would be appreciated

First off im on a HP Pavilion dv8000 laptop running with a 250gb Kaser external HDD which i can only install Ubuntu to the External HDD (internal is for work only) and here is the partition setup that im thinking about using at this point in time:

180gb - Windows NTFS (primary) NTFS
2gb - Linux Swap (primary) EXT3
10gb - Linux Root (primary) EXT3

In an Extended Partition
31gb - Sharded linux/Windows Fat32
15gb - Linux/Home EXT3
5gb - Linux/tmp EXT3
5gb - Linux/var EXT3

any thoughts/comments would be appreciated if this setup looks good or not (i found it a guide for it at (my first use of Ubuntu had a much simpler setup just containing the windows section, linux swap and a root file)

but my second question is the most important question;  Should i install GRUB to hd1 (my external hard drive) so i can boot windows automatically when my external HDD isnt hooked up

Seeing as im using a Laptop that needs to be portable, I can't have my setup such that i cant load my computer without my external hard drive attatched 

ie.   if my external HDD isnt attached i'd like my computer to boot straight to windows 

thats the problem which ultimately led to the overwriting of Ubuntu originally because if my external HDD wasnt hooked up and turned on as i booted up my computer then i got a GRUB 1.5 Error 21 and i couldnt load any OS up at all.  This in itself defeats the purpose of having a laptop in the first place so i had to get rid of grub off my MBR and get rid of Ubuntu completely just to start fresh.

Will installing GRUB to Hd1 work?

thanks in advance

---

### Post by CroEragon on 2007-01-22
I don't know about external HD newer used one but about installation:
I dont think you need separate partition for /var and for /tmp. I don't see purpose of it. Jou are just fragmenting your hard disc and with no good reason. It is wise to have /home partition, but i never met anybody on this forum to have so separate partitions for /var and /temp.
And about swap, i dont see pont of having four GB swap in two pieces. I know that laptop have 1024 RAM but still 2GB should be enough. 
And i know you got ATI Radeon XPress 200M. I have similar, without M on the end. If you need setting it up for Beryl or to enable 3D Rendering, this forum got more than few threads that deal with drivers for your card, just use search.

---

### Post by ucsdrake on 2007-01-22
oops my appologies about the linux swap ... i wrote that twice by mistake ... ive fixed it in the original post

and in the guide i read the user said it was good for security purposes ... unfortunatly i dont have the link for that guide as recently i had a mis-hap with my windows files (part of the reason im trying to move over to Linux slowly but surely) ... if im not going to use those 2 seperate partitions should i then just not use either of them?

---

### Post by CroEragon on 2007-01-22
Don't take my advice for granted. I never used  separate /var and /tmp partitions, but in about 5 months reading and posting little bit on this forum, i never saw ONE person that said that said he use separate partitions for /var and /tmp. Maybe there is some pros, you should wait little more maybe somebody smarter than me will say something.

Also, be aware that FAT32 will most likely slow down computer with it's fragmentation. You can use it, but i wouldn't on my computer. You cant store files bigger than 4 GB and cant have partition bigger than 32GB. I would use ext3 or ntfs and install drivers for Ubuntu Or windows, depends on which one you chose.

---

### Post by ucsdrake on 2007-01-22
ok, ty for the advice ... im thinking that setup is still somewhat advanced for me so i might just opt out of that ... and ive heard about just using ext3 or NTFS instead of FAT32 because of those limitations, so i might have to try that out this time as it could be quite worth the attempt to further learn the workings of linux/ubuntu

btw ty for the speedy responces


would anybody be able to help with the GRUB installation question? thanks!

---

