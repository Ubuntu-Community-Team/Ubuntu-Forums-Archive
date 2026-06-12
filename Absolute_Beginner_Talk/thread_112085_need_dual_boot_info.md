---
title: "need dual boot info"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by kgee on 2006-01-03
alright, I'm feeling pretty proud of myself to have gotten this far. I have xp and ubuntu dual booting and i even got the internet running on the ubuntu side.

now, how do i access the files on my windows partition from linux?

I have seen it done before, but that was a long time ago.

and once i pull all of my mp3's over, will they run on ubuntu?

I heard it needed some tweaking first.

help appreciated, and thanks in advance.

---

### Post by Jukey on 2006-01-03
is the partiton of windows XP NTFS or FAT32?

check by right-clicking your C:\ drive on your windows side and click properties. it will say NTFS or FAT32

please reply :)

---

### Post by Omnios on 2006-01-03
You have to mount the ntfs drive which is read only as there are diffuculties writing to ntfs with Linux (may damage, currupt ntfs). You may read and write Fat32 though. 

 This link is how to mount windrives in Linux. You should be ble to copy and run your mp3 files from your win drive but wont be able to srite them to yuor ntfs drive.

[http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs")

 Counting on your set up you might want to look into making a Fat32 partition for your documents as I found this usefull as I have a larg ntfs/fat32 drive partioned and a seperate Linux drive, just a thought you might want to look into.

---

### Post by kgee on 2006-01-03
[QUOTE=Jukey]is the partiton of windows XP NTFS or FAT32?

check by right-clicking your C:\ drive on your windows side and click properties. it will say NTFS or FAT32

please reply :)[/QUOTE]

sorry for the lack of technical info...

im using NTFS, 80 gig maxtor with 2 partitions (one os /partition)

---

### Post by meborc on 2006-01-03
for further help try this page [users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/") it mostly deals with dual bood, but also with mounting other file systems... ;)

---

### Post by kgee on 2006-01-03
[QUOTE=Omnios]You have to mount the ntfs drive which is read only as there are diffuculties writing to ntfs with Linux (may damage, currupt ntfs). You may read and write Fat32 though. 

 This link is how to mount windrives in Linux. You should be ble to copy and run your mp3 files from your win drive but wont be able to srite them to yuor ntfs drive.

[http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs")

 Counting on your set up you might want to look into making a Fat32 partition for your documents as I found this usefull as I have a larg ntfs/fat32 drive partioned and a seperate Linux drive, just a thought you might want to look into.[/QUOTE]

thanks for the info :)

I'm not planning on moving much back to my windows partition... as soon as i start to become fluent with linux i think i will dump it alltogether.

i just dont want to have to burn everything to disk to move it from one side to the next.

---

### Post by john_spiral on 2006-01-03
Hi Kgee

give the below links a try, looks quite easy:

[How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?]("http://www.ubuntuguide.org/#automountntfs")

caio

Johne

---

### Post by kgee on 2006-01-03
well, got it working :D :D :D 

thanks a million, people. Linux is starting to feel a little more natural every minute.

until next time,
party hard :)

---

### Post by kgee on 2006-01-03
Woah, one small glitch.

between rebooting, checking my windows partition, and booting back to ubuntu,

the partition unmounted itself in ubuntu.

is there a way to keep it there permanently, or at least something that dosnt require me to remount it through terminal every time?

---

### Post by kgee on 2006-01-03
Woah, one small glitch.

between rebooting, checking my windows partition, and booting back to ubuntu,

the partition unmounted itself in ubuntu.

is there a way to keep it there permanently, or at least something that dosnt require me to remount it through terminal every time?

P.S.

in case it is something im doing while mounting the partition, heres what i did

windows partition:

sudo mount /dev/sda1 /windows -t ntfs -o nls=utf8,umask=0222

other harddrive partition:

sudo mount /dev/hda2 /storage

---

### Post by Omnios on 2006-01-03
This is the same ubuntu guide as before but there is a part in it to  open fstab with gedit and add something to the file which is basicly the same info you entered just make shure you have the right partitions /dev/sda1 and /dev/hda2. Fstab is to mount your disks on start up otherwise they are unmounted wneh you log out.

---

### Post by Chipmunk on 2006-01-03
To make the partition mount every time, I think you can put the command in /etc/fstab [use gedit or vi, make a backup etc]

First, make a directory in /media called 'windows' so you have /media/windows (or whatever you wish to call it, say /media/redmondware) :D

Then sudo gedit /etc/fstab, save a backup, and add the following to the end of the file:
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0  

(change any references if they don't apply in your case, such as the hard drive number if it's different, the folder name etc)
I got this from [http://ubuntuguide.org/](http://ubuntuguide.org/)  and it worked great when I had this system set for dual boot:)

---

### Post by jimrz on 2006-01-03
you need to go back to [http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs") and scroll further down the page (below the portion on FAT32) to the part where you make a new directory for your win partition and then backup/edit /etc/fstab. This will cause the drivee to auto mount when you spin up ubuntu

edit - yes your mp3's will work, thogh you may need to go get the win32 codecs and some other stuff installed first, if you have not already done

---

### Post by kgee on 2006-01-03
alright :) 

I got my music going, I have my internet going, and I'm starting to get the hang of a few terminal commands...

Thanks for all the help guys, I'll experiment from here, and I'll probably be back next time I hit a brick wall ;)

---

