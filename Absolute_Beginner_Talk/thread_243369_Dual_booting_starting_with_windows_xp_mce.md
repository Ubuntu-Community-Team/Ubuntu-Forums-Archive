---
title: "Dual booting starting with windows xp mce"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by GonZo1323 on 2006-08-24
Im fairly new to ubuntu had it on my old machine maybe a week or to and love it, but i need my xp mce so i can stream videos to my xbox 360.
I would really like to have a dual boot, but i dont want to lose all my music and movies on my hard drive and i have no way of backing anything up, and also need the abilty to stream movies and music to my 360.:mad:  (<<<i love run on sentances)
Any suggestions?

---

### Post by orb9220 on 2006-08-24
First off you have to give more info.
How many hardrives?
How many partitions?
How much free space left on HD?
Where is movies and music is it on seprate HD?
Can Help if we are given more info.

---

### Post by GonZo1323 on 2006-08-25
Oh sorry
2 Hard Drives 
one is a slave and its like 98% full
the master has like 100gbs left (would like to use as much as i can on music)
my master has 1 partition with xp mce
i have some music and movies on the slave, some on the master (don't want to lose any)

---

### Post by L_o_N_e_R on 2006-08-25
> **GonZo1323 said:**
> Oh sorry
2 Hard Drives 
one is a slave and its like 98% full
the master has like 100gbs left (would like to use as much as i can on music)
my master has 1 partition with xp mce
i have some music and movies on the slave, some on the master (don't want to lose any)

lets see here

ubuntu need a minium of 2 gigabytes of space and thats just the system files

time to delete some old files buddy

---

### Post by GonZo1323 on 2006-08-25
But why i have around 100 gigabytes left on my master

---

### Post by Greycloak on 2006-08-25
I might be mistaken, but you should be able to resize the partition on the master drive in order to give you enough room to install Ubuntu.  My system is dual boot, but Ubuntu resides on my secondary drive.

I used Partition Magic from windows to resize my partitions, but Ubuntu's partition utility might be able to do it for you.  Whatever you do, make sure that you have all of your important data backed up.

---

### Post by eternalis on 2006-08-25
Well, you have 100GB free right?
So you can use a free partition editing software (check here: [http://www.thefreecountry.com/utilities/partitioneditors.shtml](http://www.thefreecountry.com/utilities/partitioneditors.shtml)) to resize your existing Master partition. So you can use the free space to make a Linux  Root 2GB partition (minimum) and a 256MB (minimum) swap partition. Then you will use up less than 3GB from you 100GB free space, which gives you plenty of room for music.

Hope this helped,

---

### Post by GonZo1323 on 2006-08-25
ya this helps alot im just worried about lossing all that music if i partition it with a free windows program is there a chance i could loose all my music?

---

### Post by Jerome36 on 2006-08-25
So you already have MCE installed on your main drive, correct?  It should be pretty easy to get your computer to dual-boot.  You'll just have to setup a partition on your master drive, which still has around 100 gigs left.

I just recently setup my sister's computer, to dual boot Windows and Ubuntu, though she only has one hard drive.  I defragged the drive, in Windows and then put in the Ubuntu Live CD (Dapper Drake).  After double clicking the Install icon on the desktop you're taken through a few steps, and then it gets to the part where you pick a drive and how to partition it.  I selected the option to let Ubuntu find the largest empty section, and then a slider appeared which let me raise or lower the amount of space to set aside for Ubuntu.

Her computer has a small drive and I believe I gave Ubuntu like 6 gigs.  It created the root partition and a small swap partition automatically and also installed the GRUB boot manager, which will let you select which OS to boot into, at startup.  There was really nothing to it.

I don't know what you plan to do with Ubuntu, so the amount of space you partition will be up to you.  Like L_o_N_e_R said, you're going to need at least 2 gigs, but if you want to install new software, then you'll definitely want to allocate much more.

---

### Post by GonZo1323 on 2006-08-25
i follow you 100% except defregment is that needed?
and i tought defraging is kinda dangerues and any easy way to lose files

one more thing can i access music and movies on my windows partition from linux?

---

### Post by L_o_N_e_R on 2006-08-25
> **GonZo1323 said:**
> But why i have around 100 gigabytes left on my master

o my bad i thought u said 100 megabytes lol  ](*,) ](*,) ](*,) 


yes you can acess files from windows but you have to mount the drive first

---

### Post by Greycloak on 2006-08-25
Defragging is not dangerous at all.  I defragment my windows partitions several times a week and have never had a problem.

You should be able to access your windows partitions. I have three NTFS partitions that are accessible (read only) through Ubuntu. I didn't even need to mount anything.  I installed Ubuntu and the partitions immediately appeared on my desktop. FAT32 partitions should be read/write accessible.

---

### Post by Jerome36 on 2006-08-25
> **GonZo1323 said:**
> i follow you 100% except defregment is that needed?
and i tought defraging is kinda dangerues and any easy way to lose files

one more thing can i access music and movies on my windows partition from linux?

Well, when Ubuntu looks for the largest free space on the drive, I'm sure the more fragmented your drive is (ie, the more the files are scattered) the smaller the free space will be, when it looks for the biggest open spot.  I'd think it'd be best to defrag the drive, and get the files in a more "continuous form," and you're left with a much larger free space to setup your new partition.

Disk Defragmenter isn't dangerous at all.  In all my years of using it, from Windows XP to Win 95, I've never had any problems with it.

As far as being able to access music and movies on the Windows partition, yes, you'll be able to in Linux.  I think you have to install/setup something else, but I'm not certain (somebody else will have to answer that).  My Linux computer is seperate from my Windows machine, and I access the files over the LAN, via Samba.  I know you can, but I just don't know if Ubuntu can do that automatically, without any other packages added, after the install.

---

### Post by ThatKnicker on 2006-08-25
I almost have the same problem

---

### Post by GonZo1323 on 2006-08-25
Ok thanks you guys have been a major help in me gettin away from windows:D :) :wink: :biggrin: , now im going to go hunt down some information on access windows files from linux.

---

