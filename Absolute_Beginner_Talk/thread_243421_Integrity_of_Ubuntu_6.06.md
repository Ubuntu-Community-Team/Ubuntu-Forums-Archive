---
title: "Integrity of Ubuntu 6.06"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by DoomScythe on 2006-08-25
Hi Ubuntu community,

I am an entirely new user to the Linux world who have recently decided to try and savour the taste of Linux. :) After going around the Internet for a few days, I have decided to give Ubuntu a try. Therefore, I would very much appreciate some help from the experts on this problem that I have. 

I just downloaded Ubuntu into my hard disk a few hours ago and was very excited to get started. I immediately burned the ISO image into a CD, without first checking the MD5 sum. Realising my mistake, I checked the MD5 sum using a program called winMd5sum. To my dismay, the MD5 sum did not match the one that was published on the Singapore FTP site, [http://ftp.science.nus.edu.sg/linux/ubuntu-ISO/6.06/](http://ftp.science.nus.edu.sg/linux/ubuntu-ISO/6.06/).

I then ran the Ubuntu CD on my desktop and selected the option "Check CD for Defects". The results returned 0 errors. Now, this is weird, as to my understanding, if the MD5 sum did not match initially, the "Check CD for Defects" should return some form of error in its results.

The MD5 sum provided by the FTP is fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
whereas the MD5 sum of my download is e2e5e0bfb2edffd2ce02dd77bda4558e. 

Is there anyone out there that could enlighten this newbie here? I am just an average user who have some experience in Windows but am totally blank when it comes to Linux.

Thanks in advance.

Yours truly,
DoomScythe

p/s: I am currently downloading the ISO image once more(it is seriously not nice waiting for 4 hours for the download to complete).

---

### Post by A2A on 2006-08-25
DoomScythe, welcome to the forums and thanks for choosing Ubuntu.

This is really wierd, it's a first for me to hear that the md5sum mismatches, but the CD test passes.  Nonetheless, can you manage to run the live CD and "try out" ubuntu?  Give it a shot, might be worth the try.

Another choice would be to try "md5sums" and see what it says.  
[http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/)

Let us know what status is.

Regards,

---

### Post by DoomScythe on 2006-08-25
Hi A2A and thanks for the welcome.

I have tried the program you mentioned above but the MD5 sum generated is still the same as the one given by winMd5sum. I am a little worried to try Ubuntu on my laptop since the MD5 sum does not match. I fear that it may result in a error that will cause irreversible damage to my files.

I am now waiting for my second download of Ubuntu to finish. I will check the MD5 sum again once it is done. Thanks for your quick response. Really appreciate it.

---

### Post by Amablue on 2006-08-25
The live CD can be used without fear of damaging anything. Unless you initiate the install program on the desktop no changes will be made to your computer, so feel free to play around a bit. 

Make sure though, no matter how well prepared you are, to keep your windows disks and back-ups of all your files you absolutely need to have just in case something does go wrong.

---

### Post by DoomScythe on 2006-08-25
Okay, I have finished downloaded my second copy of Ubuntu 6.06 for Desktop. The MD5 checksum generated is the same as the first download, e2e5e0bfb2edffd2ce02dd77bda4558e. Now, this is truly odd. Either the file provided by the Singapore FTP is tainted or they have forgetten to change the MD5 sum file. 

Can someone shed some light into this matter? Or perhaps provide me with a link to report my problem to the relevant people.

Yours truly,
DoomScythe

---

### Post by shyQ on 2006-08-25
> The MD5 sum provided by the FTP is fb3af44c21f1f68cc25fda7edb8c1bd3 ubuntu-6.06.1-desktop-i386.iso
whereas the MD5 sum of my download is e2e5e0bfb2edffd2ce02dd77bda4558e. 


Doom,

I don't remember my MD5SUM values (I'm writing from work right now), but I got the same problem.  It appears that the 6.06 MD5SUM file is missing - try downloading Ubuntu 6.06.1 - I got a good checksum with that version.

J.

---

### Post by A2A on 2006-08-25
DoomScythe:
It's really too bad that you encountered this problem.  Another option would be to download the 6.06.1 ALTERNATE iso image (from a source other than Singapore).  Since sometimes the normal desktop version does not work for users- depending on their machine hardware, etc, it's better to have the alternate CD handy.

Yet another option would be to download the iso image of your choice via torrent, because it checks the file for you automatically.

The third option would be to visit [https://shipit.ubuntu.com](https://shipit.ubuntu.com) and order a few CD's with various iso images.  This is a free service and will not cost you anything.

Last of all, as Amablue says : 
> The live CD can be used without fear of damaging anything. Unless you initiate the install program on the desktop no changes will be made to your computer, so feel free to play around a bit. 

I should add, if the CD's image tester passes then the CD should be fine.  If you're installing to a seperate drive OR seperate partition, go ahead and give it a shot.  Just make sure you choose the correct partition and do not overwrite your Windows partition.

If possible, back up your Windows partition to a DVD or a few CD's.

Let us know what happens.
Regards,

---

### Post by steve.horsley on 2006-08-25
There have been instances of mirrors being tainted with malware - deliberately altered ISOs (I forget which distro), so it may be worth cross-checking the md5sum files with other repos. And don't use a file that doesn't sum correctly - you don't know what it'll do.

---

### Post by DoomScythe on 2006-08-27
> **shyQ said:**
> Doom,

I don't remember my MD5SUM values (I'm writing from work right now), but I got the same problem.  It appears that the 6.06 MD5SUM file is missing - try downloading Ubuntu 6.06.1 - I got a good checksum with that version.

J.

Version 6.0.6.1? I thought the latest version is 6.06? Isn't it so or am I missing something here. Anyway, I have decided to download through Bittorrent. If the checksum is different again, I am really lost. I am really interested in giving Ubuntu a try but if this first step of mine into the Ubuntu world is already giving me trouble, I might have to think twice.

Regarding the suggestion to order a CD, I might do that later. 

Yours truly,
DoomScythe

---

### Post by Frank Golden on 2006-08-27
> **DoomScythe said:**
> Version 6.0.6.1? I thought the latest version is 6.06? Isn't it so or am I missing something here. Anyway, I have decided to download through Bittorrent. If the checksum is different again, I am really lost. I am really interested in giving Ubuntu a try but if this first step of mine into the Ubuntu world is already giving me trouble, I might have to think twice.

Regarding the suggestion to order a CD, I might do that later. 

Yours truly,
DoomScythe

Try a different mirror. Do you have to use the Singapore site?
Check the MD5 sum published from another mirror for your file.
I would think the files would be identical on all mirrors. After all isn't that what a mirror is?
I would however be leery about using a file that doesn't checksum anyway.
Just my guess but if a CD burned with this .iso don't
show errors then the published MD5 sum info may be wrong for that mirror, after all the info was input by mere humans.
Again be careful.

The Ubuntu 6.06.1 LTS is a recent release
which rolls up the (literally hundreds) of security patches and other updates that have occured since the June release of 6.06.
If you install with any 6.06 CD you will have to sit through
a lot of updates. There have only been a few updates since 6.06.1
came out so if you install with 6.06.1 you will only have to endure a few updates.

---

### Post by DoomScythe on 2006-08-27
Thanks for your reply. The reason I use the Singapore FTP is because it is very fast. Anyway, I am now downloading my third copy of Ubuntu (Version 6.0.6.1) through Bittorrent. :-)

---

### Post by Frank Golden on 2006-08-27
> **DoomScythe said:**
> Thanks for your reply. The reason I use the Singapore FTP is because it is very fast. Anyway, I am now downloading my third copy of Ubuntu (Version 6.0.6.1) through Bittorrent. :-)Kool, keep us posted.

---

### Post by DoomScythe on 2006-08-28
Okay, I think this is the biggest mistake I ever made in my computing history. First and foremost, I would like to thank all of you for taking your time off to reply. I really appreciate it. 

The problem that I have for the MD5 checksum stems from the fact that the previous 2 copies that I have downloaded were version 6.0.6 whereas the checksum that was provided was for Version 6.0.6.1. :oops:  So, what I have been doing is checking the wrong file for the wrong checksum. Really guys, this is my stupidest mistake. Really embarassed with it. Hahahhaha.....

Anyway, I am now burning Version 6.0.6.1 onto a new disc and will test it out very soon. Thanks again.

Yours truly,
DoomScythe

---

### Post by Anduu on 2006-08-28
Hehe glad to hear you sorted that out :p

I hope Ubuntu is as good to you as it has been to me ;)

Have fun !!!

---

### Post by Frank Golden on 2006-08-28
> **Anduu said:**
> Hehe glad to hear you sorted that out :p

I hope Ubuntu is as good to you as it has been to me ;)

Have fun !!!
We are after all mostly humam, right?:p

---

