---
title: "[SOLVED] Blank Screen at start of XP setup"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Mukaeutsu on 2007-09-06
Hi, so i realized that i will need to install windows before ubuntu for the dual boot to work as seamless as i wanted, so 1st i went to theubuntu 7.04 live cd to destroy all partitions (but it wanted me to install which i did not want quite yet)

So i move to my XP Home SP2 setup disk, and it says
"Setup is detecting your hardware configurations" then goes blank (instead of the standard blue setup screen)
I then tried my SP1 setup disc, same results

i had my 80gb HDD partitioned as:
ext3 200 mb /boot
xxxx ~12 gb empty (reserved for windows)
ext3 8 gb / (ubuntu install)
ext3 56 gb /hda5 (shared media)
swap 3 gb 

my goal for the new install after better understanding what i wanted:
NTFS ~10gb WINDOWS with ext2/3 r/w
ext3  ~10gb Ubuntu 7.04 AMD64
ext3  ~57.5gb Shared Media
swap ~  2.5gb

it is my belief that maybe the /boot at the beginning of the disk is hindering setup, but i am unsure, i am using 1 good condition sp2 and a near mint condition sp1

any and all help will be greatly appreciated, i am very excited to get this started (once i can)

---

### Post by toidi on 2007-09-06
Not sure this will work but you could give it a try.

When you boot your xp disk hit f6 to go into recovery mode. 
Boot to the recovery console and then do a 
```
fdisk /mbr 
```

That will repair your Master Boot Record on your drive.

If it works reboot to your xp setup and hopefully it will be installable from there.

I might be way off the mark but it is all I can think of atm.

---

### Post by Mukaeutsu on 2007-09-06
great thanks toidi, i will try that (as of now i am relocating the install of ubuntu temporarily, away from the 1st sectors of the disk, if that fails i will do that.) should have the install disc in or no disc? keep in mind that as of now i have no windows install on my computer, just ubuntu

---

### Post by toidi on 2007-09-06
From what I have read it is best to sort out the windows install first. ie. a clean install of xp/vista/2k.
Run a defrag in windows (twice) and proceed to use ubuntu live cd with gparted to partition and install your linux os.

Ofcourse you can use fdisk to setup partitions for you before you install xp or ubuntu.
Alas it has been many years since I have had to do such a thing, but I do believe it is still rather simple if you know what you are doing ;)

---

### Post by Mukaeutsu on 2007-09-06
yeah, im setting up windows now
it seemed to have worked by moving linux off of the 1st sectors

i then used fdisk and deleted the linux partitions and am starting with just the xp install, then will defragx2 and set up ubuntu

hopefully all works out ^_^
you have helped a ton through my install process, thanks i appreciate it, if anything more gets in the way, i will let you know

---

### Post by bliffle on 2007-09-06
you're on the right track. Install XP first and then ubuntu.

I just finished several days of struggle to move an old XP from a 12g HDD to a new 80g HDD so I can add ubuntu with a dual boot.

So I got the XP copied. Now I hafta figure how to get the laptop to boot off a USB CD player.

---

### Post by Mukaeutsu on 2007-09-06
alright! im up and running with XP, Ubuntu and my file storage
now to get stuff working Y_Y haha

---

### Post by toidi on 2007-09-06
Nice to hear you got it working, also nice to see you 'solved' it.  Always a good thing :D

---

