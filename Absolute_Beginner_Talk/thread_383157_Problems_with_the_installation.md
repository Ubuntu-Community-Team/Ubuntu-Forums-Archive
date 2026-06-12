---
title: "Problems with the installation"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-12
Hey! I'm new to this, i'm trying to install ubuntu, but when I get to the point where it asked how do i want to partition the disk, i chose the first option, to resize and use freed space, so i chose that option, then after new partition size, theres a horizantal line where i can move the thing and the size changes... so i didnt really know what to do, so i took the smaller size... then after like 2 mins, the forward icon was not white anymore, so i pressed it, and theres nothing happening now... the forward button is white again... and the round cursor (that tells me i have to wait) is there. It's been a long time now... i've done this now 3 times.. always does the same thing, what am I doing wrong? Thanks for the help!

---

### Post by halitech on 2007-03-12
I'm assuming you have a windows partition you want to keep?

before you started the install, did you do a complete defrag on your windows partition?

---

### Post by siciliancasanova on 2007-03-12
In windows explorer view the properties of the c drive and click on tools I believe.  Then there will be a button to run a check disk.  It will ask you to restart your machine and it will run it when your machine boots.  It will let you know if you have any bad clusters on your drive which will (in my experience) prevent Ubuntu from creating a dual boot.

---

### Post by julie_lebou on 2007-03-12
ishh... umm here's the deal, i've been trying windows vista for a while, a trial, now they want me to activate (i'm broke) and I CAN'T access ANYTHING on my computer! So I can't go defrag my drive, or go in tools... anything... I really don't know what to do, I think most of my important stuff is on my external drive, but I would still want to keep my stuff, I still have stuff I wouldn't mind to keep. But if my only option is to erase everything... i'll do it, but not if there's an answer to my problem. Is it normal that nothing is happening?

---

### Post by siciliancasanova on 2007-03-12
Actually yes it is normal if your machine has been in use for a while, it is wise to defrag and run chkdsk on your machine to make it in optimal condition for a partition.  As far as saving your stuff, I will let someone else take that I have only been using Ubuntu for a week.

---

### Post by julie_lebou on 2007-03-12
Thanks for the help anyways dude! I'm gonna go to bed now, i've been trying this for hours now, really tired, if anybody knows what I should do, write away, i'll check tomorrow... Fingers crossed! 

Thanks again!

---

### Post by halitech on 2007-03-12
got to love a company that can hold you hostage from your data. :(

try running the live cd and see if you can backup your data to your external drive (I hope it's FAT32) and then you can let ubuntu use the whole drive

---

### Post by noob_saioke45601 on 2007-03-12
i have this same exact problem. but i even did a disk defrag and a check disk and still does it.

---

### Post by halitech on 2007-03-12
is the drive FAT32 or NTFS?

have you tried downloading the gparted live cd and using that to do your partitioning first?

---

### Post by siciliancasanova on 2007-03-12
Try [this thread]("http://ubuntuforums.org/showthread.php?t=376262&highlight=dual+boot"), if it doesnt help search Dual Boot in the thread search and there are many people who may have gone through what you have and have solved the problem.

---

### Post by noob_saioke45601 on 2007-03-13
> **halitech said:**
> is the drive FAT32 or NTFS?

have you tried downloading the gparted live cd and using that to do your partitioning first?

my drive is NTFS and i havent tried gparted but i tried partition magic 8 pro.

---

### Post by halitech on 2007-03-13
not sure how well gparted will work with NTFS, haven't used it myself for that. 

do you have a blank partition already created with partition magic?

---

### Post by noob_saioke45601 on 2007-03-13
well no but it doesnt seem to work right. ill just get gparted if theres any tutorials to use it. paritition magic keeps locking up when i try to create one :(.
in themeanwhile whats a good program for backing up data? i dont wanna do a parition without backing up data first.

---

### Post by halitech on 2007-03-13
make sure you do the defrag first and it's pretty self explanatory to use gparted, even I figured it out on the first shot without being able to use a mouse :)

---

### Post by noob_saioke45601 on 2007-03-13
alright still have like 9 minutes to download gparted but ill give it a shot. thanks for the help :)

---

### Post by noob_saioke45601 on 2007-03-13
lol sorry but im a complete noob. i booted from cd and got to the partition part but no idea how to resize and add a partition for linux. if you dont mind is there a step by steper that shows how to resize a 52.5gb hard drive and add a new parition for ubuntu?

---

### Post by julie_lebou on 2007-03-13
OK, I dunno if someone can help me, but from other post, I went in terminal to find my windows file, I types this:

sudo mkdir /media/windows 

and got this:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14592   117210208+   7  HPFS/NTFS

Now the guy in the post say after paste this: 

sudo mkdir /media/windows
sudo mount /dev/hdb1 /media/windows -t ntfs -o nls=utf8,umask=0222

I got this:

ubuntu@ubuntu:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
ubuntu@ubuntu:~$ sudo mount /dev/hdb1 /media/windows -t ntfs -o nls=utf8,umask=0222
mount: special device /dev/hdb1 does not exist
ubuntu@ubuntu:~$ 

HELP! It seems there is a way to get my files, but how?

Oh and by the way, the file FAT 32... what i found anyways, when i click on the file, its only a mini text document.. so yeah, really new to this code crap lol!

---

### Post by pilot779 on 2007-03-13
hello 
im new user in world of linux system one by one day by day i have some real good experince how operating the linux , but some problem is the treminal and if i download any softwear in desktop i cant know what i have to do 
like friendly windos 

pleas email me the instruction 
or any home page can teaching 

thanks

---

