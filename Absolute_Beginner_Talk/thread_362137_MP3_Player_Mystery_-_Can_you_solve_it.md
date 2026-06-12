---
title: "MP3 Player Mystery - Can you solve it"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-02-15
Okay here is a wild and wooly one for someone to solve.

I have an MPIO music player (2 gig.) It is formatted FAT.

I can use 25% of the space. After that Linux says it is full and I can no longer transfer any music. If I fire up windows - everything works fine. 

Why is LINUX telling me that there is space left - tons of it and rightfully so.... and why could I transfer up to 25% of the disk and now I cannot?:popcorn:

---

### Post by scwinn on 2007-02-15
I have an MPIO MP3 player (2 gig) formatted FAT. When it gets 25% full Linux no longer lets me transfer music saying the device is full. Windows has no problem with it. I want to blow away my Windows partition, but IO cannot until this is resolved.:popcorn: 

Thanks

---

### Post by anders.149 on 2007-02-15
Easy. You have propably deleted files on it and they are still left there. Try emptying the trash while your mp3 player are connected. Should solve it.

---

### Post by bichopro on 2007-02-15
go to "see hiden files" and delete the files on trash folder :)

---

### Post by kelbizzle on 2007-02-15
yea I'm sure this is it. It would happen with my thumbdrive.

---

### Post by anders.149 on 2007-02-15
I have had the same problem too a few times. After X number of times I finally learned it. :) 
Those of us that came from Windows expects that files removed from any portable (and ofcourse writable) media is removed completly while Linux creates a hidden trash where it save files that's been removed. It might be better to keep the trash on removable drives un-hidden so newcomers don't get more confused than they already are. ;)

Sorry for my bad spelling. I'm Swedish and it's not my primary language.

---

### Post by scwinn on 2007-02-15
While I thank everyone for the replies... they are not correct (or perhaps I do not understand..)

The device is brand new. I started to transfer music. After transfering about 100 songs it gave me the "device is full warning". I booted into Windows. I transfered another 20 songs. I went back into Linux same problem. Then I tried to delete one file. That worked.

The mystery continues....:lolflag:

---

### Post by anders.149 on 2007-02-15
To bad that it didn't solve it. =/

When you use your player in windows, do you need to install anything to use it or do you just plug it in?

---

### Post by scwinn on 2007-02-15
Nope:KS

---

### Post by tonyr1988 on 2007-02-15
Is Linux reporting the size accurately? Right-click and Properties and look at Contents: and Free Space: and see which one is messed up. I'm assuming either:

1) It thinks it's only capable of < 2GB, or
2) It think it's already got 2GB of files on it.

That may help people help you better. It's all one 2GB FAT partition, right? It's not doing some goofy Windows-y-only thing, is it? (you can see the partitions on your computer with "sudo fdisk -l")

---

### Post by scwinn on 2007-02-16
This is getting to be more of a mystery. Who can figure it out?

When I use KDE I can transfer files to my heart's content. When I use GNOME its full. What gives?????

---

### Post by BrianH_1 on 2008-01-17
This is a pretty old thread but has anyone sorted it out? 
 
I have a MPIO FY600 (1 GB) with firmware updated to 1.13 due to previous issues on NT.

I have tried a number of things and the results I get do not seem to be consistent although I think I am doing things the same.

Sometimes when I put on a folder with a few MP3 files on it, in Windows then go to the machine with Ubuntu 7.10 and immediately look at the properties of the FY600 it will show the overall size as correct and say  for example 459.2 MB of free space.  I copy a folder with say 6 MP3 files (total folder size say 121.5 MB) and it will start copying then stop with an error that there is not enough space.  It copies the folder but only 4 of the actual files (total size 87.3 MB) before the error.  All folders are visible and the files inside play properly.  But when I look at the properties of the FY 600 now it shows as full with 0 free space.  The FY600 startup screen also shows it is full and so does Windows NT.  The only way to get the space back on the FY600 (that I have found) is to go to the Windows machine and reformat the FY600.  This is not as a result of the "delete to hidden trash file" discussed earlier in this thread - That took me  while to sort out too.

At other occasions when it stops with the "full" error the folder may not be openable (file is corrupted error) or I can open the folder but the actual files will not play (file is corrupted). Neither the FY 600 or Windows will play the files but they are visible.  Reformat the FY 600 using Windows machine to get it back to normal. 

On other tries when it stops with the "full" error the folders are visible on the FY 600 when you look using the Ubuntu machine but they are not visible on the FY 600 itself or when you look at it in Windows.  Again the only way I have found to get the FY 600 back to  a functional condition  is to reformat it on the Windows machine.

Hopefully all this will give someone more knowledgeable than I some clues to solve this issue.

Any help would be most appreciated - I totally new with Linux

Thanks

---

