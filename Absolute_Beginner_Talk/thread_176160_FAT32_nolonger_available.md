---
title: "FAT32 nolonger available?"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2006-05-14
Hi all,
today i have another problem ](*,) 

I recently tried to update my 5.04 to 5.10 (wich didn't completely work)
So when i tried to reboot, i got no GUI no more (X wouldn't start)

But normally, when X doesn't start, you can choose if you want to see the cause... so i selected "yes" and instead of a reason, i get nothing (read: no letters etc...) My screen just went gray :confused: 

I recently downloaded Mepis (because i hose my Ubuntu like every 2 days)
and i tried to write it to disc. Unfortunately my pc went blank (just after downloading)

So i tried to write it via terminal to my FAT32 HDD (wich "worked")
The ISO was copied to my hdd, but right after that, my screen went berserk.
No more letters for me, just gibberish. When i tried to read my hdd via windows, it said it wasn't formatted :-? 

I thought my MBR was kinda messed up, so i decided to rewrite it (windows cd => fixbmr) but to no avail... Still got the same message from windows (and Ubuntu doesn't recognize it aswell)

Do any of you know how i can save my FAT32 ?
Would be superb :KS 


Iarwain

---

### Post by Gimbo on 2006-05-14
Well, if you can't read it from either Ubuntu or Windows, there must be something wrong with your FAT32 drive. Just to clarify, is it a whole Hard Disk Drive formatted as one big FAT32 partition, or is it just a FAT32 partition on your main hard drive? The amount of problems you list suggests to me you might be better off formatting the whole lot and starting again. Was it just the ISO image you had on the hard drive or have you got precious data on there as well?

---

### Post by Iarwain ben-adar on 2006-05-14
It is a HDD partitioned in a 90Gb FAT32 and 30Gb NTFS.
It was quite the data on my hdd, and i would regret it firmly should i lose it.

As soon as i get my data of the drive, i'm gonna format it completely to ext3...


Iarwain

---

### Post by manicka on 2006-05-14
Restore grub using this method

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

then when back in ubuntu at the command line, run:

```
sudo dpkg-reconfigure xserver-xorg
```

Once your back in X it sounds like you'll be able to see the fat32 partition just fine. If not post your /etc/fstab

Windows won't be able to see that partition unless it actually made it and formatted it in the first place

---

### Post by Iarwain ben-adar on 2006-05-14
Thanks!
I'll try it first thing after school tomorrow.

Glad that this forum is full with smart and helpful people :-)

Cheers,


Iarwain

---

### Post by manicka on 2006-05-14
This post may also help

[http://ubuntuforums.org/showpost.php?p=1016524&postcount=2](http://ubuntuforums.org/showpost.php?p=1016524&postcount=2)

---

### Post by Iarwain ben-adar on 2006-05-16
Ok,
sorry for the delay, but school demanded some attention...

Anyways, i couldn't sudo dpkg -reconfigure xserver-xorg because it said it was conflicting (the -reconfigure option) Said something about upgrading and removing...

I did dselect => configure and got my GUI back, but alas, almost nothing works (no internet, no sound, no terminal...)

And for my HDD, i made it in Windows, but now i think it's just the read table (if such thing exists) is erased for my FAT partition (hence it can't be read anymore).

Should anyone know a way to fix the FAT-problem, i'd be very grateful


Cheers,


Iarwain

---

### Post by manicka on 2006-05-17
Windows won't recognise a fat32 partition unless it actually made it.... typical

You could try accessing the fat32 partition with a Knoppix live cd

[http://cdimage.ubuntu.com/releases/dapper/flight-7/](http://cdimage.ubuntu.com/releases/dapper/flight-7/)

---

### Post by Iarwain ben-adar on 2006-05-17
I don't think it will work, as Windows nor Ubuntu can access the drive (i also tried with Ubuntu live)

Isn't there a way to make my OS know what kind of partition is?


Iarwain

---

### Post by Sef on 2006-05-17
If you can download this rescue disk, you might be able to get your data off your hard drive.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by Iarwain ben-adar on 2006-05-17
Thanks for the reply,
but i already tried a live-cd, but to avail...


Iarwain

---

