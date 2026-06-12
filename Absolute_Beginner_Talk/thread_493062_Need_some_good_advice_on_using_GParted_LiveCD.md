---
title: "Need some good advice on using GParted LiveCD"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-07-05
Thank you for responding.

I have two HDDs installed on my computer. One HDD has Windows XP. The other HDD has Feisty Fawn.

When I installed Feisty Fawn, I chose to install it using the entire HDD. Now, I would like to partition the HDD to install Windows XP on a separate partition so that I can use Wine and possibly create a third partition to try out different Linux distros. I may have room for a fourth partition.

> Question One: Will GParted allow me to choose which HDD I want to partition without having to disconnect the other one?> Question Two: The HDD which has Feisty Fawn has 160GBytes. If I partition the HDD with four partitions, what is the best way to divide the four partitions?
Window XP partition size?
Feisty Fawn partition size?
A Second Linux Distro partition size?
A Data storage partition size?Or, do you have a better way to divide the HDD. 

BTW, I think when I installed Feisty Fawn, I was told that only 145 GB were available. 

> Question Three: Since one doesn't defrag Linux, will GParted have any problem finding all the files of Feisty and move/keep them in the correct partition?
Thank you again for your assistance. I look forward to learning how to partition using GParted.
kh

---

### Post by kuja on 2007-07-05
1) Yes
2) I'd say....
Windows ~ 10-30 (20 average?)gb
Linux 1 ~ 10-15gb
Linux 2 ~ 10-15gb
Data: whatever's leftover
3) It shouldn't have any trouble.

Also

149GiB = 160GB

149GiB = 1024 * 1024 * 1024 * 149
160GB = 1000 * 1000 * 1000 * 160

Or something like that. Those two should end up roughly equal ...

---

### Post by kittyhawk63 on 2007-07-05
> **kuja said:**
> 1) Yes
2) I'd say....
Windows ~ 10-30 (20 average?)gb
Linux 1 ~ 10-15gb
Linux 2 ~ 10-15gb
Data: whatever's leftover
3) It shouldn't have any trouble.
Also
149GiB = 160GB
149GiB = 1024 * 1024 * 1024 * 149
160GB = 1000 * 1000 * 1000 * 160
Or something like that. Those two should end up roughly equal ...

Kuja,
Thanks for the information on GParted and the info on the GiBs.
kh

---

### Post by overdrank on 2007-07-05
> **kittyhawk63 said:**
> Kuja,
Thanks for the information on GParted and the info on the GiBs.
kh

HI I would like to say that if you want to have more than 3 partitions on one drive the one has to be a extend partition and then create partitions within the extended partition. :KS

---

### Post by kittyhawk63 on 2007-07-05
> **overdrank said:**
> HI I would like to say that if you want to have more than 3 partitions on one drive the one has to be a extend partition and then create partitions within the extended partition. :KS

OK!  Thanks for that info. I'm still reading up on how to use GParted. But your information and Kuja's will come in very good use. Thanks again to you both. BTW, if you're still there: Do you mean the HDD has to be set up as an extend partition and then divide that partition into sub partitions?
kh

---

### Post by kittyhawk63 on 2007-07-05
bump...
OK! Thanks for that info. I'm still reading up on how to use GParted. But your information and Kuja's will come in very good use. Thanks again to you both. BTW, if you're still there: **Do you mean the "entire" HDD has to be set up as an extend partition and then divide that partition into sub partitions?**
kh

---

### Post by eternalsword on 2007-07-05
by the way, you should not use a windows install for using with wine...things will not work well like that.

---

### Post by overdrank on 2007-07-05
> **kittyhawk63 said:**
> bump...
OK! Thanks for that info. I'm still reading up on how to use GParted. But your information and Kuja's will come in very good use. Thanks again to you both. BTW, if you're still there: **Do you mean the "entire" HDD has to be set up as an extend partition and then divide that partition into sub partitions?**
kh

No what I am saying is that if you tried to create a 4th partition gparted would not let you, One of the partition you create has to be a extended partition then you could have 2 other partitions on that drive and also have 3 (I believe) under the extended partition. ;)

---

### Post by kittyhawk63 on 2007-07-05
> **eternalsword said:**
> by the way, you should not use a windows install for using with wine...things will not work well like that.

Ok. Can you tell me why, and if you are correct, can WINE locate my Windows' programs on the other HDD?
kh
?

---

### Post by kittyhawk63 on 2007-07-05
> **overdrank said:**
> No what I am saying is that if you tried to create a 4th partition gparted would not let you, One of the partition you create has to be a extended partition then you could have 2 other partitions on that drive and also have 3 (I believe) under the extended partition. ;)


Got it. Thank you for clearing this up for me.
kh

---

### Post by eternalsword on 2007-07-05
> **kittyhawk63 said:**
> Ok. Can you tell me why, and if you are correct, can WINE locate my Windows' programs on the other HDD?
kh
?

because wine has it's own registry.  unless the programs are portable (standalone exe files) then it would be like trying to run programs across a network share between windows systems.  best thing to do is to actually install the apps you want for wine.  there's also no guarantee that wine will not trash a given program, so it's best to make sure it actually works.

---

### Post by kittyhawk63 on 2007-07-05
> **eternalsword said:**
> because wine has it's own registry.  unless the programs are portable (standalone exe files) then it would be like trying to run programs across a network share between windows systems.  best thing to do is to actually install the apps you want for wine.  there's also no guarantee that wine will not trash a given program, so it's best to make sure it actually works.

So, are you telling me if I want to use a Window's program with Linux (and the program will work with Linux), I need to load the Windows' program on the Linux HDD? Is that correct? And if this is correct, where would I install it? Would I install it, let's say, into a separate partition?
kh

---

### Post by kittyhawk63 on 2007-07-05
If I want to use a Windows' program with WINE (assuming it works with Linux), where is the best place to install the program? Should I install to a separate partition on my Linux HDD? Or, do I install it in one of the Linux folders?

One of the programs I would like to use is Word because I do quite a bit of editing for authors who will use nothing other than Word. OpenOffice will not do some of the special formatting that some of the authors use. That keeps me from abandoning Windows XP altogether. 

kh

---

### Post by kittyhawk63 on 2007-07-05
.

---

### Post by kuja on 2007-07-05
> **overdrank said:**
> No what I am saying is that if you tried to create a 4th partition gparted would not let you, One of the partition you create has to be a extended partition then you could have 2 other partitions on that drive and also have 3 (I believe) under the extended partition. ;)

You can actually have an enourmous amount of partions in the extended partition. I forget where I heard the number before but I believe it was at least in the hundreds, way more than you'd ever need. I have six in my extended partition on one of my drives.

---

### Post by kittyhawk63 on 2007-07-05
[quote=kuja;2967737]1) Yes
2) I'd say....
Windows ~ 10-30 (20 average?)gb
Linux 1 ~ 10-15gb
Linux 2 ~ 10-15gb
Data: whatever's leftover


OK! Here's the result of running GParted LiveCD for the first time.

.............................................Size.......................Used.....................Unused
/dev/hda1.......ext3.......85.38 GiB...............4.56 GiB.................80.82 GiB..(boot)
/dev/hda3.......ext2.......21.53 GiB...............390.15 MiB.............21.15 GiB
/dev/hda4.......ext2.......20.10 GiB...............367.41 MiB.............19.74 Gib
Unallocated.................20.59 GiB................----------...................----------
/dev/hda2.......ext2........1.44 GiB................----------...................----------
/dev/hda5 Linux-Swap....1.44 GiB...............----------...................----------

I was unable to decrease the /dev/hda1 any smaller. Any suggestions on how I can decrease its size?

---

### Post by eternalsword on 2007-07-06
> **kittyhawk63 said:**
> If I want to use a Windows' program with WINE (assuming it works with Linux), where is the best place to install the program? Should I install to a separate partition on my Linux HDD? Or, do I install it in one of the Linux folders?

One of the programs I would like to use is Word because I do quite a bit of editing for authors who will use nothing other than Word. OpenOffice will not do some of the special formatting that some of the authors use. That keeps me from abandoning Windows XP altogether. 

kh

First of all, I would suggest you run a virtual machine for stuff like Microsoft Office, but if you really want to go the route of wine, you may want to look into Crossover  [http://www.codeweavers.com/](http://www.codeweavers.com/) which is based on wine, but they have official support for 6 months to a year depending on what you purchase.  You can of course try wine first before purchasing crossover to see if you can get it to work.

When installing windows programs with wine, wine creates a virtual in your home folder, so your C:\ drive is located somewhere like ~/.wine/drive_c so it would typically install stuff at "~/.wine/drive_c/Program Files"

you may be able to change where it finds the drive_c, but I've never attempted that. (you may be able to create a symbolic link but I've never tried that either)

before you install anything with wine, you should run the winecfg program.  press alt+f2 and enter winecfg, then set it up how you want.

to install Microsoft Office, you would stick in the install cd, then you would open up a terminal.  I don't know how your system is set up, but if you're using the default ubuntu, then the cd should have automatically mounted.  Open up nautilus and make sure that it is mounted.  in the terminal, you will have to change directories to wherever the setup.exe is located on the install cd.  To change directories in the terminal 
```
cd /path/to/directory
```
you may need to put the path within quotes if it has spaces or special characters.

once you are in the directory where the setup.exe is, run 
```
wine setup.exe
``` 
then it should bring up the installer that you are familiar with.

Again, I would recommend running a virtual machine, it should eliminate alot of headaches.  You can get a virtual machine running for free using vmware.

Cheers

---

