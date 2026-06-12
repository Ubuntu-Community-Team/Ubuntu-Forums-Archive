---
title: "Lost  data pls help"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by TLL on 2007-07-05
HI all

I`m a begginer at this and I have a huuuuuge problem.
I had windows/suse 10.2, and I wanted to try ubuntu.
I poped in the dvd and wasn`t to patient and I just keept hiting next................(silly me)
and now all my data is lost from former OS.
I have a 250 g hdd 3 partitions +1 for suse(or at least I used to have before ubuntu),
now I have 1 partition.
So it seams tht i have lost all data (3 years of geathering infos, documentarys, datasheets, schematics, etc
I only had about 30 g of free space aproximatly), and I feel I`m going craaaaaaaaaazy.
And I was wondering if there is a softwere like data recovery for ntfs and fat 32 only this time for linux partitions.
Or any usefull info about what could I do.
U can mail me at   laco93yahoo.com

Thanks in advance

---

### Post by dfreer on 2007-07-05
This thread should be stickied, and the name of the thread retitled to *Why you should **NOT** just keep hitting next through an install.* :D

You might be able to recover some data, the important thing to do right now is to:
(1). Turn off the machine.
(2). Grab and run a Linux Live CD, so you can connect to the internet/get help/use your PC WITHOUT using your hard drive.

The important thing here to realize is that the more you use the hard drive, the less likely you are going to recover your data.

EDIT: also, please note that you shouldn't ask people to email you, for one you won't benefit from the discussion within the thread (if someone tells you to "enter this ZYX command", and types it wrong, no one on the forum can jump in and say "no, the command should be XYZ". 
Also, it gives the impression that you can't be bothered to check the forum :D

---

### Post by TLL on 2007-07-05
Thanks for u`r reply

Yes I know that the more I use the hdd the less chance I have of recovery.
I have instaled ubuntu from live dvd but my modem is not working :(.
I have a motorola sbv 5120 ...so unfurtunuatly I cant go asking for help via net.
And yes I know I was  stupid ..... but I was so tired(just got home from office) and was eating , watching tv , and instaling ubuntu.
Thanks for u`r opinion I will try when I get home and will reply  the result, but i`m pesimistic about it:(.

---

### Post by dfreer on 2007-07-05
Ok, I'd say the main thing to do now is:

(1) Verify that all of the partitions were overwritten, and ubuntu was installed. From the live CD, start with an:
```
sudo fdisk -l
```
Post the results of that along with what you can remember about your previous partition scheme (sizes, filesystem formats, etc).
(2) Determine how important the data is to you.
If it is irreplaceable and absolutely needed, consider hiring a professional data recovery specialist (NOT a local computer repair shop). If the data isn't worth the several hundred dollars required (may be more than that, idk), you can attempt to recover it yourself.

I've done plenty of stupid things myself, including wiping (figuratively) at least 2 hard drives with semi-important data on it. Luckily I hadn't used the drive in the one case, and since the "wipe" had only changed the partition table info I was able to just restore the partition info. In another case I had DVD backup's so I didn't lose as much, just new files. It happens to all of us :D

---

### Post by TLL on 2007-07-05
1) 
My initial partition was 30-50-170 ntfs.
After I`ve instaled suse 30-30-20-170 ntfs-linux-ntfs-ntfs
After ubuntu only one partition, fresh instal no updates 211g free(ubuntu needs39g????? I think not)


2)

It is important to me because I`ve had infested aproximatly 3 years of netsurfing and gathering info.......but it is not ireplaceble....(another 2-3 years and it`s back:)  )--so i want to try to do this myself(i consider it a challenge).
I think I olny did something whit the partition table info and formating but since I didn`t overwrite on the hdd I still hope that I can recover at least 80 %.
I will try **sudo fdisk -l** and post result as son as i get home and then back to work(probably tomorow).

---

### Post by TLL on 2007-07-05
loool
infested=invested:))))))))

---

### Post by moredhel on 2007-07-05
there is an edit post button you know ;)

---

### Post by TLL on 2007-07-05
Yes there is........but then it would not been so funny;)

---

### Post by dfreer on 2007-07-05
> **TLL said:**
> 1) 
My initial partition was 30-50-170 ntfs.
After I`ve instaled suse 30-30-20-170 ntfs-linux-ntfs-ntfs
After ubuntu only one partition, fresh instal no updates 211g free(ubuntu needs39g????? I think not)

> **TLL said:**
> 
I think I olny did something whit the partition table info and formating but since I didn`t overwrite on the hdd I still hope that I can recover at least 80 %.

If you JUST partitioned/formatted using ubuntu, and didn't actually install files, you can pretty much recover everything from my understanding. I believe ubuntu simply quick formats, which just changes the partition information at the beginning of the drive, without actually touching the data itself. So basically the data would be there, you would just need to recreate the partition tables EXACTLY like they were.

But if you are able to currently use ubuntu after it is installed, it means it wrote approx 2-3 Gb's of data to the hard drive, possibly on top of your old data. Once again, the data should (mostly) still be there, you would just need to find a tool to get the good data out.

BTW, anything you can do with the currently installed ubuntu you should be able to do with the Live CD (except for use the CD/DVD drive that is in use ;) ), and since you don't have any other OS on your PC atm you might as well use the Live CD/DVD exclusively. You can install everything short of a new kernel in RAM.

EDIT: infested data.... oh geez :D

---

### Post by TLL on 2007-07-06
After all I think I am going to buy a shiny new hdd(250g sata2) instal xp pro on it and try to recover with get data back or some softwere like that.
I did a scan of my hdd on another pc with xp pro amd found moust of lost data but could not cover since softwere was not licesed.
Tell you more probably monday .
Chears

---

### Post by TLL on 2007-07-07
All good neeeeeeeeews!!:))
I`ve got myself a new hdd (250g sata2) instaled xp pro and GET DATA BACK FOR NTFS and recovered 200g 
of data(as far as I can tell 99% of my lost data).
So now I am going to instal on one drive ubuntu and the other xp........but I sens that \\\i am gone have some questions about drivers, espacialy modem driver (motorola sbv 5120).


Chears

---

### Post by dfreer on 2007-07-07
Great! I'll have to remember that software, if it worked so well. Good luck with Ubuntu in the future!

---

### Post by ltk5 on 2007-07-07
Sorry for poppin' in like that, but I jsut recently found this topic. As I have also suffered data loss - only on my USB drive...

I wonder, does any data recovery software for linux exist?

---

### Post by TLL on 2007-07-09
yes there is
if i remeber it right ...it is r-linux.
try google-ing it.....

---

