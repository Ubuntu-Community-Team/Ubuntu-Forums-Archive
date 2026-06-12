---
title: "Strange happenings....grub,xp install"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-30
Hi...as some might know i killed both my xp and ubu installs recently.

eventually managed to just install ubunto back to the main hd and left xp off as i did`nt have bootable cd.

Well the missus wants her xp so today i managed to use the xp cd i had with a 98 startup disk and installed it in dos mode...

I only done this after completely wiping all  the ext3,swap and fat32 off with the gparted cd and creating new partitions consisting of the first third of the disc for xp then ext3 and the  linux swap.

So i then do the install of xp and get all the way to restarting my pc to continue the setup and i get a grub loading error 17 message.HOW the hell d`that happen??

So is there a way to get round this so i can continue the xp setup then get my ubunto back on.....OR will the xp setup be messed and need done all again(THAT was hard work).

Im currently loading the ubunto live cd again to look see if any data`s showing up on the xp partition but im going to be pretty stuck on knowing what to do if there is indeed anything can be done...

Ive spent the last week losing both xp and ubunto but managing to get ubunto back and being quite happy BUT the wife would like her xp back and ive managed to get THIS far with a non bootable xp cd and just need a bit o help completing the process IF it can be completed......

---

### Post by PPAAUULL on 2006-08-30
Ok this is probobly caused because you had Ubuntu and GRUB installed before XP. What you have to do is install GRUB again so that you get XP on the list and you get no errors.

---

### Post by xpod on 2006-08-30
Mabey in explaining wrong...the hd used to have XP and i had ubunto on a slave but when i had the recent calamity of losing both i opted to leave out the slave and just installed ubunto onto the main hd(this too with some trouble).

Now that ive sussed out using my non-bootable xp disc i used the Gparted live cd to completely wipe the harddrive and made three new partitions from scratch......The first one being where ive started the xp install..

So there should`nt have been no trace of grub surely??

[ATTACH]15086[/ATTACH]

---

### Post by PPAAUULL on 2006-08-30
Ok seeing as you have nothing on the drive. Repartition it with the XP install aswell as reformat it. Tell me if that works.

---

### Post by xpod on 2006-08-30
Ive just spent the last 3 hours installing xp to that first partition supposedly.....(i did`nt use "smartdrive" so you can imagine how long it took).

I DID reformat and i DID repartion before i carried out the install.
I aint done the ubunto again yet so i dont know how grub was even still 
there to prevent me rebooting to continue with an already LONG xp install.

Thats why i wiped ubunto off so i could do all the "xp first" thing then do the ubunto install again on the second space??

---

### Post by PPAAUULL on 2006-08-30
Did you or did you not use gparted to do your partitions?

---

### Post by xpod on 2006-08-30
Yes i did.........I asuimed that was the easiest way to completely wipe them then make new ones then reinstall...xp first then ubunto.

I know how to wipe a disk with fdisk(and a bootdisk)but does this mean i need to go do it all again and partition with fdisk before i put any linux or gparted stuff near it....

It`s slowly dawning on me i think...lol

In just see everybody being told to use gparted live cd and did`nt see the problem

---

### Post by PPAAUULL on 2006-08-30
Ok I will tell you what I did. I installed XP USING THE XP DISK TO REFORMAT AND PARTITION THE DRIVE. That means that there was a XP partition and another blank one. I then used the blank one to put Ubuntu on. Worked without a problem. That is what I am purposing for you to do. 

GET IT?????

---

### Post by xpod on 2006-08-30
Yes i get it but i dont think you do.I DONT have an xp cd as such..

All i have is a copy of my 1386 directory as data on a burned cd...It`s not a proper xp disk....It`s one i made from my setup files on the computer.

It`s quite ok to install xp with but there aint no partitioning stuff on it.

The only way i can make partitions is with fdisk or with gparted or similar.

Unless im missing something here......Which is quite normal for moi

---

### Post by PPAAUULL on 2006-08-30
oh.... can you not get a hold of an XP disk?

---

### Post by xpod on 2006-08-30
Oh dear........if you knew how many times ive been asked THAT question in the last five months or so that i was using xp.Prior to moving over here 2 weeks ago i had spent my first few months on pc`s trying to make the slipstreamed sp2 cd from the copy of xp i had on the drive(now on cd)

I even managed to redirect the sfc /scannow function to use my hd copy instead of requesting an xp cd-rom BUT i never did quite manage to make OR borrow one.....I never needed to once sfc had tidied it all up.

And i still should`nt need to.........I`ll go away AGAIN and wipe it with fdisk and then im sure i`ll figure out making the partitions with it.

I just assumed using gparted to make a fat32 on the first half of the hd would be fine.....I managed to copy all my xp setup files(5ooo+)
to the disk with  a 98 bootdisk and get to winnt.exe and install.

It took over 2 hours to install but no data showing up in gparted is something im familiar with even though it probably there.

Im going to go do it all again without the gparted if i can...I just hoped there was a simple thing i could do from here.I did`nt know just wiping & partitioning with gparted cd would leave a grub problem without even getting to the ubunto install.

---

