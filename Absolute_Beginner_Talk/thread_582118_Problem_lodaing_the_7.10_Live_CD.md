---
title: "Problem lodaing the 7.10 Live CD"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Filosoof on 2007-10-19
Hi there ! I just downloaded the Gutsy Gibbon and burned it to cd, to try it out. When i booted from the cd and started the live cd, i can only get pass the loading screen. Then it starts to throw bunch of errors at me, which look similar to this:
 [2**.******] Buffer I/O error on device sr0, logical block 2*****
And i got some SQUASHFS errors too.
I'm quite a beginner with this, so i don't know what to do now. I've burned different cd's using ImgBurn and Nero. I can get the cd done with Nero, but it stops at 67% of verifying the cd with Imgburn.

---

### Post by Lord_Dicranius on 2007-10-19
You may wanna check the integrity of the download:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Filosoof on 2007-10-19
Well the ISO file passed with flying colours.

[IMG]http://xs220.xs.to/xs220/07426/hashythingy.PNG[/IMG]

*MD5 Check Sums are the same.*

---

### Post by Lord_Dicranius on 2007-10-20
Sounds like it may be something to do with the CDs and/or the burning process itself.  My first assumption was the ISO, but judging by the MD5 checksum, that checks out.  I find it odd that the ISO will burning using Nero, but won't finish verifying when using Imgburn.  Does Imgburn give you any errors when it stops at 67%?  Maybe try getting a CD from a friend, or burning it on a different PC..?

---

### Post by Filosoof on 2007-10-20
Yes, ImgBurn gives me an error and i will try to post it later. I have used 3 different kind cd's: i have used my acme cd-rw several times, 2x Verbatim (cd-r) and 1x acme (cd-r) , which are useless now. I'm starting to think that the problem is in my DVD-ROM/CD-RW device, but that doesn't explain why it does it with nero and not with ImgBurn. The possibilities i see are:
 1) using a friends pc to burn the iso
 2)try to download a new ISO

---

### Post by Perfect Storm on 2007-10-20
Also try another download mirror or better yet using torrent - as they less likely going to mess up.

Here's some good advise I give newcomers:

**Some good advise for newbies:**

1) Wait a month before installing the latest version of X,Y,Z distro after its release.

2) Have seperated /home *(a good idea is to have / (root),  /home and /boot)*

3) Go for Clean install - *(no matter which OS, an upgrade is hazardious, especially if you have non-official libs/apps installed).*

4) Download the torrent .iso - *(less likely it will be corrupt than FTP/HTTP download)*

5) Make sure the CD/DVD-drive is clean, also check the CD/DVD for damaging and dirt. - *(yes, this seems so obvious, but I helped alot of people where these simple step did the diffrence, note: the quality of the CD/DVD also have an impact on success rate).*

6) Check the checksum of the downloaded .iso.

7) Burn the CD/DVD at 4x speed and verify.

8 ) When inserting the Linux CD got to the "verify" option, and let it check itself - *(this avoid you to install a borked version).*

==============
**Troubleshooting**

a) If it continously fail regarding borked CD, mismath checksum, download the .iso from another mirror - *(I have been there where one of the mirrors had a bad .iso)*.

b) If check and verify is okay and it still fail to install/load go for the alternate CD instead - which have text installer. - *(It's much more stabil and not difficult if you read and follow the text installer guide)*

c) Check your memory for bad sections - *(yes, your hardware may have failure)*

d) ATI cards - Nothing new here, always been a struggle regardless which Linux distro. But that will change soon (hopefully) as the driver goes Open Source .

e) Intel cards - clumbsyness and/or slow respond - install : libgl1-mesa-dri

---

### Post by Filosoof on 2007-10-20
Ok here is the ImgBurn error.
[IMG]http://xs320.xs.to/xs320/07426/ImgBurnError.PNG[/IMG]

I wrote the cd with 4x speed.
Thanks Artificial Intelligence for the helping information. I quite didn't get the 2) Have seperated /home (a good idea is to have / (root), /home and /boot) advise part, cause im not familiar with the terms.
Actually i'll tell you what im going for right now. I have Windows and i thought of going over to Ubuntu. My hard drive is seperated into 2 partitions:
 1) ~15GB, has Windows on it and some programs
 2) ~60GB, has movies, music, pictures, games on it.
I want to replace the OS on the first partition and still keep my music,...etc. on the second one.I know i have to let go of the games, but thats not a big deal for me. My main problem is getting the cd working propaly, so ill try to download it with a torrent and see if anything changes.

---

### Post by Perfect Storm on 2007-10-20
> Thanks Artificial Intelligence for the helping information. I quite didn't get the 2) Have seperated /home (a good idea is to have / (root), /home and /boot) advise part, cause im not familiar with the terms.

It's when you set up your partitions for Ubuntu, you can split it so to say. / (root) is where the system files are /home where your stuff is, /boot where mbr is. By splitting it up you still have home with your stuff and settings and can still upgrade or installing a new version of ubuntu.



I can't help you about the other as I'm completly windows free (allmost 5 years now).

---

### Post by Filosoof on 2007-10-20
Ok i got it downloaded again and the problem is still there. So i figure it's most likely my DVD ROM's fault. It gives the same error in ImgBurn as before.

---

### Post by Chuck58 on 2007-10-20
I get an hdd error 2306*(something) error and then more that I don't have time to copy before my monitor goes into standby. I have 3CD's with Ubuntu 7.10 downloaded and burned from 3 different mirrors. It finally occurred to me today to run the CD test from Ubuntu start and it shows one file error on all 3 cd's. My first guess is it's NVIDIA but running a live cd, not sure how to get past it. Second guess, my 6 year old NEC Multisync A700 monitor might be too antique for Ubuntu.

I've got other flavors of Linux burned and all are fine, as is Ubuntu 7.04, KUbuntu 7.04 and all work fine.

---

### Post by Chuck58 on 2007-10-20
additional. Managed to get it all down

I got hdd:error code:0x70 sense_key:0x03 asc:0x15
Buffer I/O error on device hdd, logical disk block 288625 and 288626

Tried Casper  and same problem.

Then tried safe graphics, same problem

I switched resolution to 1024x768 and no error , just little white bar blinking in upper left corner for 5 minutes. Then, safe graphics, same screen res and Casper, went to the post office to check mail. Returned 15 min later and the little white bar was still there. Then, I gave up and decided that I'll erase Ubuntu 7.10 from my 3 CD's and use them for something else. Somewhere in all that, I tried 32 bit and even 16 bit color but no luck.

Ubuntu 7.10 just doesn't like my computer. I'll stay with 7.04 and wait for the next version.

---

### Post by Lord_Dicranius on 2007-10-20
> **Artificial Intelligence said:**
> Also try another download mirror or better yet using torrent - as they less likely going to mess up.

Here's some good advise I give newcomers:

**Some good advise for newbies:**

1) Wait a month before installing the latest version of X,Y,Z distro after its release.

2) Have seperated /home *(a good idea is to have / (root),  /home and /boot)*

3) Go for Clean install - *(no matter which OS, an upgrade is hazardious, especially if you have non-official libs/apps installed).*

4) Download the torrent .iso - *(less likely it will be corrupt than FTP/HTTP download)*

5) Make sure the CD/DVD-drive is clean, also check the CD/DVD for damaging and dirt. - *(yes, this seems so obvious, but I helped alot of people where these simple step did the diffrence, note: the quality of the CD/DVD also have an impact on success rate).*

6) Check the checksum of the downloaded .iso.

7) Burn the CD/DVD at 4x speed and verify.

8 ) When inserting the Linux CD got to the "verify" option, and let it check itself - *(this avoid you to install a borked version).*

==============
**Troubleshooting**

a) If it continously fail regarding borked CD, mismath checksum, download the .iso from another mirror - *(I have been there where one of the mirrors had a bad .iso)*.

b) If check and verify is okay and it still fail to install/load go for the alternate CD instead - which have text installer. - *(It's much more stabil and not difficult if you read and follow the text installer guide)*

c) Check your memory for bad sections - *(yes, your hardware may have failure)*

d) ATI cards - Nothing new here, always been a struggle regardless which Linux distro. But that will change soon (hopefully) as the driver goes Open Source .

e) Intel cards - clumbsyness and/or slow respond - install : libgl1-mesa-dri
That's good stuff Artificial Intelligence!  I've subscribed to the thread to keep this list handy :)

---

### Post by Perfect Storm on 2007-10-20
I have stickied one here at the beginners forum.

---

### Post by Lord_Dicranius on 2007-10-20
> **Artificial Intelligence said:**
> I have stickied one here at the beginners forum.

\\:D/

---

