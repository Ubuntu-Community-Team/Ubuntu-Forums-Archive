---
title: "arggg i have been reading... lost noob"
date: 2007-07-05
forum: Apple Intel Users
---

### Post by gahau on 2007-07-05
okok ppl i have actualy read some of the post but i am kinda lost...
i have been a pc user for most of my life recently switch to mac...
i now own a macbook with the intel chip
recently discover the wounder of ubuntu...
here is what i would like to do, i have dl a copy if the graphic instal
i would like to run ubuntu on a small portion of my current HD, i will probably allocate 8gb for ubuntu
my question is that putting ubuntu on my little mac (that is also running xp with bootcamp) will it mess up my mac and xp side, meaning will it have to erase those two partitions in order to put ubuntu on
if someone could please tell me how to instal ubuntu on my current mac without disturbing it content...


thanks thanks

---

### Post by scragar on 2007-07-05
ubuntu will give you a nice little sliding scale that let's you resize your largest/main partition to provide it with space WITHOUT erasing any of your other files.

---

### Post by grim1234 on 2007-07-05
There is a good guide here :

[http://gentoo-wiki.com/HARDWARE_Apple_MacBook](http://gentoo-wiki.com/HARDWARE_Apple_MacBook)
 
use diskutil to resize your osx partition, and use refit to boot with. That'll work better than bootcamp. you can only have three functional partitions though, so one each for osx, linux, xp is your lot.

---

### Post by gahau on 2007-07-05
so can i just put the ubuntu cd install in right away or will i have to do some werid things... to make it 3 partitions...

---

### Post by cyberdork33 on 2007-07-05
> so can i just put the ubuntu cd install in right away or will i have to do some werid things... to make it 3 partitions...

I would suggest reading the information posted just before your post on how to partition your disk.

---

### Post by gahau on 2007-07-05
> **cyberdork33 said:**
> I would suggest reading the information posted just before your post on how to partition your disk.
the thing is that i dont really want to mess with partition i was woundering (please make it that easy please) if  it could be as easy as just pop the cd in and the cd will do the work for me... that is it

---

### Post by cyberdork33 on 2007-07-05
If you are trying to triple boot, then you do not need to wipe everything, but you are probably going to have to partition at one point or another because, unless you have free space on your drive, you are going to have to resize an existing partition.

First I would install rEFIt (This will help you boot the OS you want). After that, figure out how you want to partition your drive, and read the tutorials on how to do so. All these tutorials on triple booting / how to partition your hard drive, etc. don't exist because we prefer it that way, it is because it is (unfortunately) not as simple as popping in the cd.

If you have more specific questions to ask, please do so. (Need help partitioning, need advice, etc)

---

### Post by gahau on 2007-07-05
cool! thanks man ill try that...

---

### Post by gahau on 2007-07-05
okok latest update
i ave the live cd
and i just pop it in and straight run it...
i ran from the cd and when i tried to install it was going to partition the drive that i have allocated for XP from boot camp....
i wounder in i can partition it once more with bootcamp so then i can put ubuntu then =)

what do u guys think?

---

### Post by cyberdork33 on 2007-07-05
bootcamp will only make 2 partitions

---

### Post by grim1234 on 2007-07-05
don't use bootcamp, refit is a very good bootloader and will do exactly what you need. 

take a look at the link posted above, it has lots of info about partitioning.

---

### Post by gahau on 2007-07-06
does anyone know how to delete the bootcamp partition and use refit?

---

### Post by cyberdork33 on 2007-07-06
> **gahau said:**
> does anyone know how to delete the bootcamp partition and use refit?

you shouldn't need to delete the bootcamp partition unless you are trying to get rid of windows.

---

### Post by IrunwindowsjustoforACAD on 2007-07-06
Is it possible to run the Live CD of ubuntu while i have two other OS's running on my computer via bootcamp?

Processor: 2.16 Ghz intel COre 2 Duo
Memory: 1 GB 667 MHz DDR2 SDRAM
Startup Disk: Macintosh HD
Dual Booting with Boot Camp WIndows XP
#: type name size identifier
0: GUID_partition_scheme *111.8 GB disk0
1: EFI 200.0 MB disk0s1
2: Apple_HFS Macintosh HD 91.0 GB disk0s2
3: Microsoft Basic Data Untitled 20.5 GB disk0s3

Aparently something's wrong with doing so because my Live CD won't show up in my boot Menu...unless I have refit, but it only loads windows if I click on the live CD option!!

---

### Post by cyberdork33 on 2007-07-06
please don't post multiple times. Your answer is in your first thread.

---

