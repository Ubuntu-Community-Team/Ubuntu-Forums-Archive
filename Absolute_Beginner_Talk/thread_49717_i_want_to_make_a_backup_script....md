---
title: "i want to make a backup script..."
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by glandula on 2005-07-17
i want to make a simple backup script, instead of backing up my selected folders by hand. but im not sure how.

i want to backup
/home/USERNAME/.evolution
/home/USERNAME/.gaim
etc
to /media/backup (this is a hdd)

and i want to make sure all subdirs and files are copied. how would such a script look?

also are there any arguments i could add to force overwrite, incremental backup etc?

i also understand that such a script must be made executable. how?
---
and then i need a restore script doing the opposite

any help and a small sample script just to see how it should look would be appreacaited :)

---

### Post by dave9191 on 2005-07-17
Rsync is the answer to all your questions. 

go to a command line and type 'man rsync' to find out about all the options that this programs has. Ive only started to use it recently, but it does have an incremental backup feature. Ive never used the backup or incremental backup features tho, just a plain simple copy. 

rsync -az -progress /home/USERNAME/ /media/backup/

should copy and preserver everything in your home directory (inc subfolders) to the backup folder. It will also tell you how much is left to copy. I backup over ssh to another machine using those options. If you read the man pages it will tell you how to speisify which folder to include and which ones to exclude. Its quite a long man page that i havent read through properly yet. 

The great thing about this app is that it only copies over the differences, so after the first rsync, the others will be lightning fast :)

If you need more help just ask :)

Dave

---

### Post by glandula on 2005-07-17
[QUOTE=][/QUOTE]
 hi, thanks for the help!

rsync seems to work juse fine except i see no info about how much left to copy. i also wonder if this, executed like u suggested above, will delete files in the dest dir if they have been deleted from the original folder since the last backup

anyway my major problem with this is that it goes so incredibly slow and eats all of my cpu, i cant even play mp3s when rsync is running. in fact ive noticed tthat my backup hdd is very slow in ubuntu. ive got 2 satas, 1 80gb where ubuntu is installed, and one 160 gb for movies etc. copynig between these is very fast and smooth. but the backup hdd which is a 120 gb IDE, its a pain copying to and from it even though the partition is ext3 (like my other partitions). the IDE also contains a fat32 windows partition with my windows stuff in case i ever want to install windows again (doesent look like i ever will though, maybe if theres a really good game i want to play some day)
ive messed a bit with the dma settings based on the cd/dvd dma instructions, but its not any better. anyway, thats probably a question for another thread

---

### Post by dave9191 on 2005-07-17
I left a - out of the command. You need --progress as opposed to -progress. As for the file delete thing, Im not sure. I know that one of the rsync options will do that, but im not sure that the archieve (a) option will do that. Ill have to test and experiment. 

Well the good thing about rsync is that after the first backup, it doesnt take long to perform sequential ones (depending how many files there are and how much they changed). 

It uses a little bit of cpu to make comparisons, but shouldnt eay all of your cpu (of course it depends what cpu you have). I have a 1.5 Ghz laptop and while rsyncing and playing mp3's it peaks at 100% sometimes, but most of the time the cpu usage is 20-50%. Mp3s play smoothly for me.

You could minmise the load on the cpu a little by dropping the z option. It compresses the files before moving them to save on transfer size, great for doing it over a network (like me), but not so useful when doing it from one drive to another. 

But not being able to play mp3s while doing the transfer might be due to the hdd beind in use so much and the comp cant read them in fast enough. The hdd speeds and such would be an issue for another thread tho :) 

Dave

---

### Post by dave9191 on 2005-07-18
If you run rsync like that it will not remove file in the destination directory that are no longer in the source directory. I tested it out. If you want it to delete files that no loger exist in your home directory from the backup fir you need to add the 

--delete 

option. But this might delete more then its supposed if not used properly. Read the man page about this. 

Dave

---

