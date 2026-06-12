---
title: "installing ubuntu on an hp pavillion"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Stalker2432 on 2007-05-01
hallo, im new, so hello to everyone, im completely beginner in linux/unix but even windows.
Now i want to install ubuntu on an HP Pavillion t3240.it

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00570418&lc=it&cc=it&dlc=it&softwareitem=pv-42566-1&product=1154281&os=228&lang=it](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00570418&lc=it&cc=it&dlc=it&softwareitem=pv-42566-1&product=1154281&os=228&lang=it)

that link show the charachteristichs of my computer.
I have it from more than a year, but now i want to install gnu/linux with ubuntu 7.04

here's my question:

my computer has an HD of 250 GB

Partitioned in 2 part:

1) HP_Pavillion (System) 225 GB (66,8 free)
2) HP_Recovery 6,95 GB

I have downloaded Ubuntu tryout disk, clicked on install,
but when it say to create a partition,  i dont go ahead cause i scared to delete all the data from my HD
Ive read there are some problem with this computer, cause the Recovery disk.

Id like to repartitionate the Main partition (1) and obtain an'other partition of 30/40 GB for Ubuntu in ext3, i know i have to create a Swap Partition of 512 MB too.
Now the problem is that i have no idea of how to do.

Please Help!
Should i use some repartition program? Or can i do all the process via the ubuntu installer?
I have a lot of documents and files on my main partition and so i dont want to format it.
Thanks a lot, id like to have suggestion too, from people that know this kind of computer pavillion with the recovery partition.

Should i buy another internal hd, so to bypass all these problems?
Thanks, im completely ignorant.

---

### Post by Billy McCann on 2007-05-01
The Ubuntu installer will prompt you through this very easily.  

There are some screenshots here.  

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

You are wanting to keep the "Recovery" partition?

---

### Post by Tomosaur on 2007-05-01
I have an HP Pavilion with a similar setup to you, although I think mine is an older version, so the hardware is a little different.

In any case - Ubuntu should install just fine. You can either repartition from within Windows, or use the partitioner within Ubuntu. A few things for you to do before you install though:

1) **Backup everything you want to keep**. Although it's unlikely - big operations like partitioning and installing a new OS always runs the risk of failure or errors. It is unlikely to happen, but it's best to take precautions.

2) Defragment Windows a few times before partitioning. This ensures that the partitioner can work well - if your disk is heavily fragmented, you run even more risk of failure, or problems later on.

3) When the time comes to install Ubuntu - if you decide to go with Feisty, there is a feature which will allow you to import stuff (Documents etc) from your existing Windows installation. I've never used that feature myself, but it could be worth looking at.

---

### Post by Stalker2432 on 2007-05-01
@Billy
thanks for the quick replay, i want to keep the recovery and i want to keep the main partition with windo XP, (ive and OEM winXP installation, so i guess that if i have some problem the recovery should help to reinstall the system, but as i sayd im completely ignorant), but from the main partition that of 225 GB, i want to obtain a 30/40 GB partition for Ubuntu.

Now the installer in not the same of those Screen shots you linked, after the Language and Keyboard setting screen, it skip directly to  step 6, "Prepare Partition".
There are not those "resize partition" screens. 

[http://img155.imageshack.us/img155/3233/w2u302wy.png](http://img155.imageshack.us/img155/3233/w2u302wy.png)
(it skips directly to a screen like this, after the language and keyboard setting)

Ive downloaded the 7.04 ubuntu CD

thanks!
I read somewhere i could used somethink called gpartion? (cause as i sayd my installer dont have that repartision screen)

@Tamosaur
Thanks for the tips!

---

### Post by Billy McCann on 2007-05-01
Stalker,

In your "Prepare Partitions" window you'll have 2 partitions listed, the recovery and the XP.  

Click on the XP partition and then choose "Resize/Move Partition".  The XP partition should show plenty of free space, especially given that you've defragmented it (you did, didn't you?).  You can drag the right side of the partition to the left to create your 30-40GB partition.  Click OK or Apply (I'm going on memory here).  Then you create the new partition out of the freed space.  Tell Ubuntu to mount this new partition to /.  

But I'm surprised that you went straight to the manual parititioning window and didn't see the "Guided Parititioning" option anywhere.  

Tell me if this isn't clear.  


Billy

---

### Post by Stalker2432 on 2007-05-01
thanks again Billy, currently im defragmenting the hd with the windows Defrag.

As i have finished (It seems to take forever, im still to 20% now after an hour), i will try again to boot from the ubuntu CD and click on install, and i will see if i can find that guided repartition  window.

Thanks a lot man.

Can't wait this defrag will be finished to try this tips!

---

### Post by Inxsible on 2007-05-01
Depending on how much you will use Ubuntu, you need to make a calculated estimate of how much space you need to assign to Ubuntu.
 
If you are gonna use the XP as your primary OS and simply use Ubuntu to get a feel for it, I'd say 30 GB would be enough. But if you plan to do a lot like install Beryl and Open Office and music players and such, you might wanna think about giving Ubuntu more space.
 
I installed Ubuntu Feisty, last night with a Windows Vista dual boot, I gave Vista 50GB and 110 GB to Ubuntu from my HDD of 160 GB.
 
I have an HP dv9000t laptop too..You can create Recovery DVD's and get rid of the HP_Recovery partition like I did. Actually I created the recovery DVD's AND took a backup of the Recovery partition onto my 500 GB external Hard drive.
 
Works great !!
 
Still need to iron out a few quirks here and there....but I am on it !!
 
Of course...you can ask questions here and someone will help you out surely !!
 
Thats the best thing about Ubuntu compared to other distros, IMHO

---

### Post by Bachstelze on 2007-05-01
30 GiB would be **far** more than enough ! With 30 GiB, you can install all the packages in the Ubuntu repos and still have plenty of extra space.

Make two partitions, one of 10 GiB where all the system files will go, and another to store your personal data, which can grow as larcge as you wish.

---

### Post by Lykele on 2007-05-01
Stalker2432 -

Like you I have a little laptop with the recovery partition.  Last night, for first time ever, I installed Ubuntu.  Of course, I did keep my fingers crossed, but everything went well.

However, I did backup the C: drive just in case something went wrong.

If you click the link below (or copy it if not shown as link) you will see a video of an install.  It gave me some confidence in doing it myself.  Even shows where the partitioning question comes in.

When I boot up I can go to Windows XP or Ubuntu.

[http://video.google.com/videoplay?docid=-2369893842637434537](http://video.google.com/videoplay?docid=-2369893842637434537)

---

### Post by Stalker2432 on 2007-05-03
thanks everyone, everythink here was usefull!

I didn't know the importance of that defrag... i never did that on my computer, it took almost all the day... as it was finished i redone a second defrag and this time it took very few time

Than i booted the disk and installed it, I used a 30 Gb partition and a 1G swap. I can choose wich system to boot like in that video, all go very fine.
My thoughts were to see if i can do in Ubuntu the same think i do in Windows, id est: Surfing the internet, play music and video from time to time, and write stuff.

I was tired of that moffice suite, so i went to download the open office for windows, this made me curious about other open-"thinks", so i thought to use open office on an open OS. After a lot of Googling, I arrived here...

Now the problem is the internet connection, ive ADSL, and sure the first think is to be able to surf on the internet like in windows.

Any link? Post in other threads? Suggestion... somethink were to start
Do i need some specific know-how to connect to the internet in Ubuntu?
I dont even know how it works in windows, the telephone company just delivered me a disk and a ADSL modem, i had to install the disk and connect the modem...

**EDIT: Ive resolved the Internet connection problem, now i can connect to the internet thanks!**

---

