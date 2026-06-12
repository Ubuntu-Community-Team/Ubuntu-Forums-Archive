---
title: "Please help! Ubuntu corrupted my data."
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Solar_989 on 2007-11-10
Hello,

I decided to try out Linux and Ubuntu for the first time dual booting. The situation is after placing two of my most important DVD+RW disks with my data for the first time in Ubuntu, the data is now corrupted. Please, could anyone help me recover this data? The DVDs have all my college work, family and friends photos, and work-related files on them.

Both DVDs still show in the properties menu the correct size of the total files and blank space. The filesystem is reported as being UDF. When I try accessing the DVDs, one DVD shows up blank, while the other DVD has some still accessible files, some filenames showing but not accessible, and some whole folders blank. Windows XP shows the same thing now.

I have even tried data recover programs for DVDs and tried to copy the DVD as an image file but the image reports it is corrupted as well.

Background info: The DVD+RW disks have been used before, and worked in Windows XP. When I placed them in Ubuntu, I noticed the DVD drive would keep blinking and spinning for a long time after the drive was mounted and accessible and thought it was weird. I was able to access the data and copy some to Ubuntu. When I tried to eject the disk, it took a while to eject it meanwhile Ubuntu was still accessing the data as if it was "finalizing a disk" as cd burning software does.

All of my data are on those DVDs because I did a fresh install of both Windows and Ubuntu.

Thank you immensely for any help you can provide.

---

### Post by geforce123 on 2007-11-10
First, to make sure it won't get even more bad, I would start by copying (remaining) data of the DVDs..

Use the dd command:
(You may need the change the dvd drive's path...)

dd if=/dev/dvd of=dvd.iso


after that, you must find some softwares that allow to get data back..  From this point I can't help you much since i've never recovered data from an linux filesystem (ext3, resierFS, etc, etc)

---

### Post by Solar_989 on 2007-11-10
Hi geforce123,

Thanks for the advice.
I tried the dd command, placing my own dvd's location, but it gives me a blank/does not work iso file.

I don't know what software I could use to recover the data on a DVD+RW. I tried one program on windows XP but while it reports no actually damage or bad areas to the disc, when it makes an iso copy, that too does not work.

---

### Post by kingof1981 on 2007-11-10
if they that's important... you should try... one of the data recovery company's... they are very helpful and have more advanced technology then vi have... and it don't cost so much only a few bucks... i had sometime long time ago the same problem... i got almost 100 % restored data back... try it...

---

### Post by Solar_989 on 2007-11-10
I guess I could contact a data recovery company, but I'm hoping to resolve the problem without it coming to that. Besides, if I do recover the data, is there a problem with Ubuntu that I will not be able to use DVD+RW?

I use them frequently and if Ubuntu continues to corrupt them, then I will have to stick with windows for now. What if a friend or someone at a job hands me data on a DVD rewritable? My computer might corrupt it as well.

I did a fresh install of Ubuntu to see if it might have been a bad install, but no difference. I made another DVD+RW in windows with useless files and it got corrupted after the first run though Ubuntu as well.

If it means anything, this is my DVD-RW drive: TEAC DV-W58E HH 8X DVD+RW

---

### Post by shad0w_walker on 2007-11-10
Just a quick question. Have you tried the discs in a different computer? It may just be some strange config issue on your install.

---

### Post by LaRoza on 2007-11-10
RW disks are flakey, and do not even work in different drives. You might (should) look into USB flash drives, they are much better.

I have never tried to use RW disks, but I have heard people on the forum speak of using them without any trouble. 

It also depends on what format they were written in to begin with, Windows formats for optical disks are weird, especially in Vista.

---

### Post by Solar_989 on 2007-11-10
I tried the DVD rewritables in another computer running windows XP and still does not work.
I know windows Vista has its own burning system but I burnt these DVD+RW in windows XP, just that the filesystem is UDF.

---

### Post by LaRoza on 2007-11-10
> **Solar_989 said:**
> I tried the DVD rewritables in another computer running windows XP and still does not work.
I know windows Vista has its own burning system but I burnt these DVD+RW in windows XP, just that the filesystem is UDF.

Can you try burning a RW disk in Ubuntu, and then see if XP can read it?

---

### Post by Paul820 on 2007-11-10
Have you tried **dvdisaster**? It's in the repos. There is an option of reading a disk and trying to rescue as much data as it can and then it puts it into an ISO file on your computer. Give it a go, i used it once for a corrupted dvdrw and it worked a treat. There is a doc file for it as well so you might want to get that also. Let us know if it works for you.

---

### Post by atlfalcons866 on 2007-11-10
whats your filesystem?

---

### Post by Solar_989 on 2007-11-10
LaRoza, I will try to burn two DVD+RW with files in Ubuntu. One disc will be placed into windows XP right after I burn it to see if it works. The second disc will be placed into Ubuntu right after completion, copy some data, eject, then placed into Windows XP to see. 

 Paul820, thanks for mentioning the dvdisaster program. I am trying it out right now in Ubuntu.

atlfalcons866, I do not know which filesystem you are referring to, I'm sorry if I give a bad response, but my Ubuntu has ext3, my windows XP has ntfs, and the DVD+RW has udf. Is that what you meant?

---

### Post by Solar_989 on 2007-11-10
Update on the situation:

1. Tried dvdisaster over and over again on both DVDs. No luck. I cannot recover the data.

2. Tried out 3 tests with burning data in Ubuntu to a DVD+RW and seeing if it can be read in Ubuntu and Windows XP. Results:

Test 1)  Used default CD/DVD creator in Ubuntu. Included images, text files, and html files. Default settings used. (I don't think you can change them in CD/DVD creator). The filesystem used was ISO 9660. 

Windows XP WITH a Drive Letter Access (DLA) program installed (to allow drag and drop burning) is able to read the data.
Windows XP PLAIN is able to read the data. 
Ubuntu is able to read the data. 

------
Test 2) Used default CD/DVD creator with default settings. Filesystem: ISO 9660. After burn was completed, I placed into Ubuntu and copied data again.

Windows XP WITH a Drive Letter Access (DLA) program installed is able to read the data.
Windows XP PLAIN is able to read data.
Ubuntu is able to read the data.
----------
Test 3) Used K3b now and set the filesystem to UDF.

Windows XP with Drive Letter Access program able to read data.
Windows XP PLAIN is able to read the data.
Ubuntu is able to read the data.

---I then placed the DVD+RW back into Windows a second time after Ubuntu accessed the files and no corruption.

*************

I believe what could have been the problem was my DVD+RW with all my important data backups were burnt using Sonic burning software with Drive Letter Access (DLA) also activated for my DVD rewritable drive. For some reason when using the UDF filesystem on such DVDs, they are corrupted after being placed into Ubuntu for the first time.

I don't know if this is enough information to perhaps warn future users that any data burnt using Sonic and/or Drive Letter Access installed with the UDF filesystem could lose their data if placed into Ubuntu?

Sonic Record Now 7.0
Drive Letter Access....I think it was version 5.0???

As for my data, I think it is unrecoverable. :(

---

### Post by LaRoza on 2007-11-10
Sorry about your data, you should keep backups from now on (on your harddisk at least).

Some burning applications do weird things, so I wouldn't be surprises if that was the cause.

---

### Post by FXEF on 2007-11-10
> **Solar_989 said:**
> I tried the DVD rewritables in another computer running windows XP and still does not work.
I know windows Vista has its own burning system but I burnt these DVD+RW in windows XP, just that the filesystem is UDF.

Most likely it's Vista causing the problem not Ubuntu.

Vista burns discs in the Live File System format by default (Ubuntu can not read this format), but you can also choose to burn discs in the Mastered format.

Mastered format should let you read the disk in Ubuntu.
:-({|=
Go here for all the details: 
[URL="http://windowshelp.microsoft.com/Windows/en-US/Help/b47eb51a-ea6d-4d97-97b0-2d07a59316981033.mspx"]http://windowshelp.microsoft.com/Windows/en-US/Help/b47eb51a-ea6d-4d97-97b0-2d07a59316981033.mspx

[/URL]

---

### Post by meindian523 on 2007-11-11
FXEF:

He burnt the DVD's in XP!not Vista.....

---

### Post by Solar_989 on 2007-11-11
FXEF, I burnt the DVDs using Windows XP, not Vista.

---

