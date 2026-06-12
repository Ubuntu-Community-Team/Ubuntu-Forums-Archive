---
title: "Help dual booting vista ubuntu"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by THe.Conundrum on 2008-03-07
can't seem to get it to work everytime i install ubuntu it messes up my vista boot and neither will boot, then i run the vista dvd and repair boot files. only problem is i can't get ubuntu to show up. i've tried using easybcd and that didn't work (probably because i don't know what i'm doing) but i now have a sucessfull install of ubuntu and vista loads my problem is i don't know how to make windows boot manager recognize the ubuntu partition.

thanks

---

### Post by JoshuaRL on 2008-03-07
Well, windows won't recognise any other OS on the drive.  That's why when you install Ubuntu, it uses GRUB (GRand Unified Bootloader).  That will allow you to boot into whatever OS you want.

So how exactly are you installing?  What steps do you go through?  And what errors do you get?

---

### Post by THe.Conundrum on 2008-03-07
well i booted it in the live cd installed it on my main hd after creating a 90gb ext3 partition and then a 3gb swap partition (manual install partition setup) it installed fine and then went to restart and then it booted to the windows boot manager and showed up some easybcd boot stuff and no windows so i repaired the windows and now it shows up as recovered but no "grub" thing at any point

---

### Post by JoshuaRL on 2008-03-07
So at what point did you use the easyBSD CD?  What were you trying to do with it?

---

### Post by Sef on 2008-03-07
With Vista, you should use its partitioner to shrink the hard drive.   If not, then you will encounter problems.

---

### Post by THe.Conundrum on 2008-03-07
easybcd not bsd [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) that was installed before i've tried to get this thing to install like 4 times and then i uninstalled easybcd and now i've tried to do it without easybcd but to no avail

---

### Post by THe.Conundrum on 2008-03-07
yes i did use vista's partitioner for that

---

### Post by lam2988 on 2008-03-07
hi, i used wubi and it install ubuntu almost on its own but it is not the 10.7 ver. easy to follow direction. i now am looking to get rid of xp.

---

### Post by marvelljones on 2008-03-07
If you have shrunk the Vista Drive already, and want to give EBCD another chance, download it and then follow these instructions:
 
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
 
I printed them out before I began, and followed them to the letter. Be sure to write down the partition you put Ubuntu on so you can make sure GRUB gets installed there. Hopefully this link helped, I use Vista Home Premium and have had no problems. Except that I still use Vista that is. :rolleyes: Oh and leave the free space unformatted, let Ubuntu format it and make sure to leave a little space for the SWAP drive (I use 1 GB for mine).  I learned that the hard way.  Hope you can get up and running soon and enjoy Ubuntu.

---

### Post by r5gtt2k3 on 2008-03-07
Hmm I'm new to Ubuntu, I have Vista on my other partition, And I have just installed (like 20 mins ago) 7.10 and i thought oh noes, my mbr !! then i quickly went out of Ubuntu, and it was there, a sigh of relief, Also, there is an app for Vista that allows you to make a boot if you wish, you can name your OS's that you boot with select the time it takes to start up blah blah, it's BCD something, Google BCD an you should get it running soothly with that

---

### Post by gpilkay on 2008-03-07
Here's a site on Vista/Ubuntu, it's from 7.04 but most of the info is probably still good:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2)

---

### Post by THe.Conundrum on 2008-03-07
well it didn't work again.... not sure why its not working perhaps when i click the advanced tab where you select bootloader maybe i'm picking the wrong drive?? (hd0) or (hd1) thats about the only thing i am not sure how to figure out

---

