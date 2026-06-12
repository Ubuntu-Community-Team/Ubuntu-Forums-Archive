---
title: "Windows Size ????"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by StephUb on 2007-11-16
Ok,
I am ready to install ubuntu in dual boot for now, after having played with the live CD a bit...
But not yet ready to kick Windows (Work related stuff where we can't find apps for linux)

My question is more... how do you shrink windows ??
I am not asking the partitioning (i am using GParted live CD), no, i am asking get rid of files to get it smaller..
Right now it's 16Gb with two games of 1.5G each..

Can i shrink more or i am good to go ?
I was thinking keeping 25-30G for windows from my 100G 7200rpm of my laptop

what do you think ????

Thanks a lot folks

---

### Post by SunnyRabbiera on 2007-11-16
well firstly did you defrag your windows?
this is important, also compressing your files on windows also helps.

---

### Post by StephUb on 2007-11-16
I am currently defragmenting using perfectdisk (win defrag is just very bad)
I removed also before defrag the hybernate and pagefile in order to be able to shrink with GParted.
i am kinda amased of the size windows need for what it's actually doing good... lol

When you say compress files, is that the box in disk properties ?

thanks

---

### Post by jryprt on 2007-11-16
Make sure you backup all your file music pictures ect. just in case thing go wrong I  know .

---

### Post by StephUb on 2007-11-16
All data are on my external HD (old 80G 4200rpm from my laptop), i cleaned 22G of mp3, 16G of work related stuff....
i am gonna try to comact the files in windows to see what i can get back....

---

### Post by SunnyRabbiera on 2007-11-16
> **StephUb said:**
> I am currently defragmenting using perfectdisk (win defrag is just very bad)
I removed also before defrag the hybernate and pagefile in order to be able to shrink with GParted.
i am kinda amased of the size windows need for what it's actually doing good... lol

When you say compress files, is that the box in disk properties ?

thanks

yup, compressing the hard drive is a biggie as windows hogs so much, I would suggest doing it as it does help with dual boots, I did that myself in my dual booting days.
but be warned compressing things can take a little while

---

### Post by StephUb on 2007-11-16
It's in the process of compressing...
After that i will run Perfect disk in smart mode
Boot on GParted to shrink windows to 20 to 30 gigs
Boot on windows to get things right
boot on Gparted to create my DATA partition (NTFS)
and then boot on ubuntu to create ubuntu 10G ext3
a /home of 5-10G ext3
the swap of 2G

Is ubuntu able to create these partitions or do i have to prepare them with G parted before hand?
Do i care what ubuntu is doing when creating the partition?
My concerns are DOS accept nly 4 primary partitions on a disk, i am planning 5 with 3 create under ubuntu or Gparted. Is that gonna mess thing up ?
Do i have to create a extended in GParted after the 2 first partitions or leave it unallocated ?

Thanks for your help

---

### Post by SunnyRabbiera on 2007-11-16
I will warn you one more thing though on compressing, you will get many annoyances in it so you are warned.

---

### Post by Romin-1 on 2007-11-16
As an after-thought I would also run CCleaner, you will be amazed at the ammount of stuff it will get rid of. It's a freebie, just Google it and go.

Jon

---

