---
title: "First time ubuntu user"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by nuwan78 on 2006-04-01
Hello,
   I am a first time ubuntu user. There are several questions I like to know first.

  1.  I am hoping to install Ubuntu with windowsXP as a dual boot system .
      Is dual boot up  possible with ubuntu?
      I am good at windowsXP but like to experiment with ubuntu ( that is go beyond the live CD of ubuntu) I have a 20GB hard disk, what will be the best way to partition it to use XP and ubuntu? 

2.   Where can I get g77 ( fortran77 version of linux) and linux version of C ?
      Are these two compatible with ubuntu 5.10?

3.   I have got several pdf  format e books and some conventional type linux books which are biased to Caldera, Redhat, Debian. Will the techniques taught in those books work on ubuntu? Where can I get ( perhaps as a free ebook) a very comprehensive book on ubuntu linux?


  Hope to hear a favourabl answer ASAP

  Regards 
  Nuwan

---

### Post by TTT_travis on 2006-04-01
[QUOTE=nuwan78]Hello,
   I am a first time ubuntu user. There are several questions I like to know first.

  1.  I am hoping to install Ubuntu with windowsXP as a dual boot system .
      Is dual boot up  possible with ubuntu?
      I am good at windowsXP but like to experiment with ubuntu ( that is go beyond the live CD of ubuntu) I have a 20GB hard disk, what will be the best way to partition it to use XP and ubuntu? 

2.   Where can I get g77 ( fortran77 version of linux) and linux version of C ?
      Are these two compatible with ubuntu 5.10?

3.   I have got several pdf  format e books and some conventional type linux books which are biased to Caldera, Redhat, Debian. Will the techniques taught in those books work on ubuntu? Where can I get ( perhaps as a free ebook) a very comprehensive book on ubuntu linux?


  Hope to hear a favourabl answer ASAP

  Regards 
  Nuwan[/QUOTE]

1. Yes it's possible, when you install Windows XP make the partition maybe half the drive or whatever you want just make sure you leave at least 3 or 4 gb for ubuntu, once windows is installed boot the ubuntu install, when it gets to partitioning use free space and that will auto install with the extra space.

2. I am not sure, I know nothing about this although it might be in one of the apt respositories 

3. Some parts of those books will help but the only book that will be close is the debian one, since ubuntu is based off debian. There are some online resources like ubuntu guide and stuff that may help a little.

---

### Post by Jedeye on 2006-04-01
this may help [https://wiki.ubuntu.com/InstallingCompilers]("https://wiki.ubuntu.com/InstallingCompilers")

---

### Post by tadashi on 2006-04-01
Fortran 77 is in the repositories.  I remember seeing it there (I remembered it because I used to use it and sometimes load it up just in case).  If you have only a 20 GB dual boot drive I would make 10 GB for the primary use OS, 5 GB for the shared data drive (format it FAT32), and 5 GB for the 2nd OS.  Linux can read NTFS but cannot write to it, but has no problems with FAT32.

You should be able to find everything here: [https://wiki.ubuntu.com](https://wiki.ubuntu.com).  Otherwise you can buy some at [http://search.barnesandnoble.com/booksearch/results.asp?WRD=ubuntu&z=y&cds2Pid=9481](http://search.barnesandnoble.com/booksearch/results.asp?WRD=ubuntu&z=y&cds2Pid=9481)

---

### Post by nuwan78 on 2006-04-03
Hey thanks guys. 

But FAT32 does it go with windows XP which i intend to use as the primary OS ( 10GB ) - which is fine for me but how can I partition the 5 GB as FAT32 when XP's default is NTFS.

---

### Post by meborc on 2006-04-03
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
- this is the bible of dual-boot... has been used since the beginning of breezy and there seems to be no problems with it...

good luck ;)

oh... and you MUST see the guide... it is in my sig!

---

### Post by catlett on 2006-04-03
Fat32 is fine for for your size hard drive, Fat 32 is the format for windows 98,ME and 2000. It is only the XP version that is NTFS. NTFS is used for large hard drives. If you are over 100 gigs in hard drive size you should use NTFS but, you can still use FAT32. There is a limit to individual file size in Fat 32. I believe it is 4gb. That shouldn't be an issue for you. The best way for you to have a dual boot system is if you have both formatted to FAT32. Windows can run it no problem and Linux can read and write to it. If you had windows at NTFS you will encounter issues trying to work with it. Linux can read NTFS and has some tools to deal with NTFS but it is easiest if you have a small hard drive to just go all FAT32.  This is a very good how to   [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Didn't see the guide was already posted.

---

