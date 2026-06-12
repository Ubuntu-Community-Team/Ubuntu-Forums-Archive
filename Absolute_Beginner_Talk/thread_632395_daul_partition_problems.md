---
title: "daul partition problems"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by dnice on 2007-12-05
I need a step by step guide to enlarge my daul boot of ubuntu and vista.. Could anyone guide me thru this?? Also could anyone tell me where i could go to find references on how to clean up ubuntu 7.10. What i means is i installed Ununtu about 2 weeks ago and been experimenting with different downloads now i want to rid my system of double applications,and unwanted programs. I dont want to delete something that i want. Thanks to all that could help me.

---

### Post by ItsMitsHere on 2007-12-05
> **dnice said:**
> I need a step by step guide to enlarge my daul boot of ubuntu and vista.. Could anyone guide me thru this?? Also could anyone tell me where i could go to find references on how to clean up ubuntu 7.10. What i means is i installed Ununtu about 2 weeks ago and been experimenting with different downloads now i want to rid my system of double applications,and unwanted programs. I dont want to delete something that i want. Thanks to all that could help me.

As for cleaning UBUNTU, go to terminal and type **sudo apt-get clean** followed by **sudo apt-get --fix-missing**. This will remove any unwanted/broaken modules/packages/dependencies and fix problems.

Then update and upgrade your system by **sudo apt-get update** and **sudo apt-get update**.

As for your experimenting thing, If you installed any new programs, you will have to remove them from synaptic and/or Add-Remove programs. 

None of above two will remove any of your data files.

How can you enlarge both partitions? I think you want to enlarge your ubuntu partition! If that is the case, you should create a backup and resize your partition with gparted (Gnome partitionar for ubuntu) or partition manager (for vista). Before knowing which partition you want to resize, it would be non-sense to write a step-by-step guide ;).

---

### Post by dnice on 2007-12-05
Hey there thank you for the information. It was very helpful. Now about enlarging Ubuntu, you are correct. On my Volume called SQ004409V05 It says i have 76.3 GB FREE of 111.0 GB. Now i only partitioned 36GB for ubuntu to begin with.It says i have 98484 items totalling 37.0 GB. Now the thing is that when i go to properties on the Toshiba it says This Volume has 138.8 GB used with 6 itmes totalling 107.2 GB with 1.3 GB free. Now i am not only new to Ubuntu but computers in general could you please exlplain what this means. After my last update the system told me that i had less then a GB of space remaining and since then the Ubuntu has been moving much slower. Apps. take longer to launch. So i guess what i am really asking is to get clarification of what this all means so that i can address the issue and feed ubuntu what it wants to  operate.Now i didnt do the math but my laptop only has 160 total so these two number dont add up. Last note is that i booted to vista and it says i have 100 GB free space.

---

### Post by ItsMitsHere on 2007-12-05
> **dnice said:**
> Hey there thank you for the information. It was very helpful. Now about enlarging Ubuntu, you are correct. On my Volume called SQ004409V05 It says i have 76.3 GB FREE of 111.0 GB. Now i only partitioned 36GB for ubuntu to begin with.It says i have 98484 items totalling 37.0 GB. Now the thing is that when i go to properties on the Toshiba it says This Volume has 138.8 GB used with 6 itmes totalling 107.2 GB with 1.3 GB free. Now i am not only new to Ubuntu but computers in general could you please exlplain what this means. After my last update the system told me that i had less then a GB of space remaining and since then the Ubuntu has been moving much slower. Apps. take longer to launch. So i guess what i am really asking is to get clarification of what this all means so that i can address the issue and feed ubuntu what it wants to  operate.Now i didnt do the math but my laptop only has 160 total so these two number dont add up. Last note is that i booted to vista and it says i have 100 GB free space.

Dnice,

Can you please tell me how does your system tell you how much free space you have?

On computers there are two kind of free space. One is free space that has not been formatted. This space needs to be formatted in order to use it. Second type is formatted free space, that is where you can store your data. 

In windows vista there are nice drive icons specifying free space, where as in Ubuntu, there is some app called disk analyzer or like in applications>accessories. Also if you open your root directory, you will get the info about total free space on the status bar at the bottom of the window.

As for your statistics, I can't comment on that untill i know how did you get those gbs. If possible also tell me how did you installed ubuntu (if vista was preinstalled), how did you partitioned the disk and how many partitions your disk has. also mention if therr are further partitions on both your os. like C:, D:.

---

### Post by dnice on 2007-12-05
Okay this is the skinny. Vista came pre installed so  i partitioned vista and formatted the partition to NTFS. The larger partition(Vista) is also completely formatted to NTFS as well. When i install Ubuntu it ask me to form  two volumes (partitions) out of the 36GB's i set aside for Ubuntu, which i did. I got a bit mixed up with the new terms so i may have made the smaller partition the folder for all the OS information for ubuntu like 10GB and the remaining 16GB were used for the rest of  ubuntu( i guess the RAM) i dont recall the term it used.  As far as checking for how much free space i have i right clicked each of the volume icons went to properties and thats where i got the numbers i gave you. Also how do  i get to the root? I did check the disk analyzer and it says total file system size is 122.3 GB and the total system usage is 31.2 % OF 38.2 GB's. I read somewhere that you could adjust this but i have been looking for hours and have not found what i needed.

Dnice

---

### Post by ItsMitsHere on 2007-12-06
Dnice,

From the info that i got from your last post i gather that out of your hard disk (which is 160 GB), There is still so much free space! Your ubuntu partition is of around 38.2 GB out of which you have utilized some 12 GB for ubuntu installation (which is around 4 GB) and any downloaded, installed programs and data while you were experimenting. Still you have left some 25 GB free on ubuntu partition.

As for vista, You must have some 4 GB used for vista installation and some working data, movies music and program installations summing up to 35 GB usages. The rest is Still free.

so the math is

UBUNTU:
12 GB used + 25 GB free=37 GB total

Vista:
35 GB used + 76 GB free=111 GB total

Hard disk:
111GB Vista + 37 GB Ubuntu=148 GB total.

Everything adds up nicely. If you are wondering about why do we get only 148 GB total when the hard disk is a 160 GB. The reason is that you spent the remaining 12 GB for the purpose of formatting and partitioning. Infect, every 40 GB needs 3-4 GB for formatting and actual usable space after formatting is 36-37 GB. 

I think you need not resize any of your partitions because you have lots of free space. In case you really want to resize, backup your data and delete ubuntu partition. resize the partitions and reinstall ubuntu. This will give you a clean environment to work in.

---

### Post by dnice on 2007-12-06
Ok, i think i understand what you're saying so when i right click on the drive marked toshiba and it says i only have 1.3 GB free what is that in reference too? If i download any new packages will it tell me i no longer have space, and lastly what are the two partitions called i know 1 is swat which i am assuming is the ubunutu OS right? Then what is the other one called and why do i need it and how large shoul this other partition really be? Thank you in advance for your help on this it is very appreciated.

Dnice

---

### Post by ItsMitsHere on 2007-12-06
Dnice,

The swap is a partition which is used to store information required by the OS temporarily to use it in conjugation with the RAM (which is a kind of very high speed memory chip). It should be between 512 MB to 1 GB. Allocating more is waste. The swap partition is used by os but OS is never on swap. 

The OS resides on the ROOT partition which is the mount point of your hard disk and is denoted by "/". You wont find any directory called root. The "/" (slash) it self is root. everything on your comp including your OS resides on root. so for instance your home folder is directly under root directory, It would be "/home" and not "/root/home". Generally you keep your personal data under home folder. the programs are kept in /usr/bin and so on for easy file keeping. however in linux you can install anything where ever you like. 

As per 1.3 GB free, you must be sure of how much space is left on your drive, 'coz you are the one who stored data on the disk. Again I would say, you are not being specific on this. The data that you have provided on your post up to this point are very ambiguous and nobody can make out any sense out of that. I have been providing you information based on guess work only. If you are completely new to computers, Get some basic learning from internet surfing and google (but not blogging). Now you are saying that you click on toshiba icon but in which os? 'coz there are so many possibilities like your C: drive in vista is called TOSHIBA or the drive is referred from UBUNTU as the whole drive. Just telling me that you clicked on toshiba drive will not give me any clue about what the hell is this toshiba drive.     

Lastly, Don't get me wrong on this, but I really don't care about appreciation, I helped you for mutual happiness and nothing else. Infect the phrase 'Your help on this is very appreciated' after asking the really silliest and stupid questions really irritates me, Instead I like simple Thanks! (u need not care about what i like and what i don't) 

I don't mind if you ask me thousand more questions, but my answers won't do any good for you unless you yourself move your *** (Censored!) and read something.

---

### Post by LowSky on 2007-12-06
> **dnice said:**
> ... Now i only partitioned 36GB for ubuntu to begin with.It says i have 98484 items totalling 37.0 GB.... Now the thing is that when i go to properties on the Toshiba it says This Volume has 138.8 GB used with 6 itmes totalling 107.2 GB with 1.3 GB free. ....Now i didnt do the math but my laptop only has 160 total so these two number dont add up. Last note is that i booted to vista and it says i have 100 GB free space.

i'm guessing your using Windows to look up this information, but what your saying is very hard to understand.

138.8 Gb is the size of the hard drive.. at least it should be
6 items (i have no ideaa why you have only 6 items, where are you reafding this from)  totaling 107.2 with 1.3 Gb free (this makes no sense)

then you say vista say you have 100GB free?

Please try to make this make more sense

---

### Post by ItsMitsHere on 2007-12-07
@LowSky

"Give a man a fish and he eats for a day, teach a man to fish and he eats for a lifetime."

Thats exactly what I'm saying!!! ;)

---

### Post by dnice on 2007-12-07
Ok, i understand what you your saying and you are correct. I will do a little research and gather a bit more understanding about this before asking a questions. Thank you.

Dnice

---

### Post by louieb on 2007-12-07
Good day. If you could post a couple of things it would give a clearer picture of you setup. Open Applications>Accessories>Terminal
1st is the partition table post the output of ```
sudo fdisk -l
```(lowercase L) 
and 2nd the free space ```
df -h
```

---

