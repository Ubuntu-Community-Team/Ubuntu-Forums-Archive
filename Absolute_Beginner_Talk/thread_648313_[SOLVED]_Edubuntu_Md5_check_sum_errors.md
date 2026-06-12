---
title: "[SOLVED] Edubuntu Md5 check sum errors"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by despidey on 2007-12-23
I'm trying to burn a disk for Edubuntu in Vista (shudder), but every time I run WinMd5Sum I get a checksum from the disc that is different from the one posted on the mirror.  I'm downloading using bit torrent and copying the iso with iso recorder.  I have done this successfully for ubuntu  and xbuntu but in 3 tries for edubuntu I still get the error and the disc checksum is always the same.

From MDSUMS
c759f0a8988b110ab18fb83f86194e38

From disc MD5Sum text file
c37fb6c02ac0ad17d55c3774420bd15b

Any ideas?

---

### Post by Sorivenul on 2007-12-23
From my knowledge, MS, especially Vista, doesn't like people burning ISOs.  This is elsewhere in these forums.  To address your problem:  First, try redownloading the ISO.  Also down load ImgBurn, it runs on Vista, and is a great alternative to any software already on the system:  [http://www.imgburn.com/]("http://www.imgburn.com/").  Good luck!  Let us know how it goes!

---

### Post by SOULRiDER on 2007-12-23
If you used bitotrrent (which you did) your iso isnt corrupted so theres a problem when burning. As sorivenul sayd, try another burning application.

---

### Post by despidey on 2007-12-23
> **SOULRiDER said:**
> If you used bitotrrent (which you did) your iso isnt corrupted so theres a problem when burning. As sorivenul sayd, try another burning application.

Did as you suggested including re-downloading from a different mirror and using ImgBurn to copy the iso.  Still got the same results.  I _did _do a checksum match between the iso on my hard drive and the listed checksum and they matched.  I also did a checksum match from one burned disc to a newer burned disc and they matched i I just can't seem to get the burned image to match the original checksum.  I haven't had this problem with either ubuntu and xbuntu.  Very strange.  

Do you think I'd have better luck trying to download and burn a disc using the Ubuntu installed on my laptop?  I'm such a newb that I'll have to go thru all the documentation first - but that's what learning is all about.  Any suggestions?

---

### Post by Sef on 2007-12-23
Sometimes getting a good iso is not easy.  Once I had to download about 6 times before I got a good download.  Bittorrent and other torrents automatically check the md5sum when downloading.

---

### Post by despidey on 2007-12-23
> **Sef said:**
> Sometimes getting a good iso is not easy.  Once I had to download about 6 times before I got a good download.  Bittorrent and other torrents automatically check the md5sum when downloading.

I don't think the problem is with the download because the checksum for the downloaded iso on my hard drive is correct.  When I burn the iso checksum have changed.  confused:

---

### Post by SOULRiDER on 2007-12-24
Boot with the disk and use the Check CD for defects option. how exactly are you getting htat md5sum?

---

### Post by despidey on 2007-12-24
> **SOULRiDER said:**
> Boot with the disk and use the Check CD for defects option. how exactly are you getting htat md5sum?

I use WinMd5Sum.  I copy and paste the checksum from [http://ubuntu-releases.cs.umn.edu/edubuntu/gutsy/MD5SUMS](http://ubuntu-releases.cs.umn.edu/edubuntu/gutsy/MD5SUMS) 
and compare it to the MD5Sum text file on the burned disc 

I have the uneasy feeling that I'm doing something wrong...something different from the previous successful burns.  It has been so easy previously and I have diligently followed the burn instructions posted by psychocat.

---

### Post by Josh1 on 2007-12-24
Is the md5 fine of the iso without mounting? Try mounting the .ISO using Daemontools or the like and doing an md5 check.

> **Sorivenul said:**
> From my knowledge, MS, especially Vista, doesn't like people burning ISOs.  This is elsewhere in these forums.  To address your problem:  First, try redownloading the ISO.  Also down load ImgBurn, it runs on Vista, and is a great alternative to any software already on the system:  [http://www.imgburn.com/]("http://www.imgburn.com/").  Good luck!  Let us know how it goes!

Lol, Microsoft hates .ISO's? I thought Microsoft gave vista as an iso to download while it was in BETA.

---

### Post by Duck2006 on 2007-12-24
If your ubuntu check sum checks then install that and then from the terminal load the edubuntu fount end.

> sudo aptitude update && sudo aptitude install edubuntu-desktop

or install the bits you want from your Synaptic Package Manager.

---

### Post by SOULRiDER on 2007-12-24
Using the check CD for defects option will check if the disc is corrupted or not, theres no need to hash any files or anything!

---

### Post by despidey on 2007-12-24
Just figured out what is wrong.....nothing!  

I've been checking the wrong checksums - been comparing from the download site to the actual burned disc instead of checking from the download site to my iso on the hard drive.  Duh!!!!

When I posted that I had this feeling that I was doing something wrong, I went back and _carefully_ read psychocat's instructions (after spending part of the nite puzzling over this) and discovered my mistake.  I'll load up edubuntu today on the computer I'm giving to my grandchildren to make sure all is well.

I'm really sorry for having taken up everybody's time with this.  I have been continually astonished by the community here and hope that I can eventually become proficient enough to help.

---

### Post by SOULRiDER on 2007-12-24
Good thing you sorted things out. Remember to markt he thread as solved.

---

### Post by despidey on 2007-12-24
Doing that now.  Thank you all again.

BTW, I now have 5 extra Edbuntu discs to give to Windows users with kids for Christmas LOL

---

### Post by SOULRiDER on 2007-12-24
> **despidey said:**
> Doing that now.  Thank you all again.

BTW, I now have 5 extra Edbuntu discs to give to Windows users with kids for Christmas LOL

Thats one awesome xmas present if you ask me :)

---

