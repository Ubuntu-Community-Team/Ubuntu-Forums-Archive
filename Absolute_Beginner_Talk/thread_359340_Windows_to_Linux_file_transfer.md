---
title: "Windows to Linux file transfer"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-02-11
I have just succesfully completed my new system, and would like to move all of my files from my windows laptop over to ubuntu. most of these are mp3 files, but some are windows programs that I would like to keep on my new system (will probably run them in WINE). What would be the easiest way to transfer these (upwards of 10 GB, so CD's are out of the question)? Thanks in advance.

---

### Post by orlox on 2007-02-11
In the repo's there is a package named something like libntfs. It can be used to acces ntfs partitions from linux, so that could be usefull to get the data you want...

---

### Post by Cardmaster91 on 2007-02-11
is your ubuntu system on your laptop? or are they two seperte computer?

im assuming two seperate computers
i would first of all recommend cds/dvds, but you said out of question for whatever reason.
if not cds, then do you have an mp3 player? or some sort of external hard drive? If you do, simply put the files on the drive, then plug it into the ubuntu and withdraw them from the drive.
Thats pretty much the only way, unless you set up a network between the two computers, which is hard and long and i have the faintest idea how to do.
or, well, you could create a photobucket account, and host the files on there, but this could take several hours, and could get you arrested since the po don't know your circumstances (if you do do this, then i suggested archiveing all the files and then hosting them)

if the two systems are on the same computer, do what he said, or you could create a new partition (ext3 dont get along with ntfs very well) by download [gparted]("http://gparted.sourceforge.net/") img file, burn to cd, and put the cd in the computer. restar, and it will run gparted. this is a patrition editor, simply resize a partition (if you dont have any unpartition space left). then create a new fat32 partitiotion (fat32 is good friends with both ntfs and ext3), about 4 or 5 gigs big (depending on how fast you want this done, or how big the files are) Then on windows you would open mycomputer, go to probably drive e (total guess there, it would be next to c:/) Sopy files to there, restart to ubuntu, open the partition you created in nautilus, and drag and drop.

i hoped this helped

---

### Post by nickburns on 2007-02-11
if they are on separate computers then install samba, and create shared folders.  It is quick and easy.

---

### Post by nickoli_02 on 2007-02-11
If both computers are connected to the same network (ie behind the same router) it should be pretty easy to set up a shared network between them. Try using Gftp, or some similar windows ftp program.

---

