---
title: "How to install ubuntu, kubuntu and edubuntu on the same pc using only the cds?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by mayank.abhishek on 2006-08-16
Help!

I want to install ubuntu, kubuntu and edubuntu on the same pc, same partition.
The pc on which I want to install is NOT connected to the internet. I have the cds of Ubuntu, kubuntu and edubuntu.

This is what I did:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

mayank@edubuntu:~$ sudo apt-cdrom add
Password:
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d9f91a1075ce140463bf88837cc07be6-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Wednesday  31 May 2006 08:46:20  using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.


mayank@edubuntu:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d251c204c5513e9470c11bf645950d27-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Wednesday  31 May 2006 09:03:59  using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.


mayank@edubuntu:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [855fab8f87a68637ee8304488b201a88-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Edubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Wednesday  31 May 2006 09:11:50  using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Edubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.


mayank@edubuntu:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop


mayank@edubuntu:~$ 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
As, you see this does not produce any result. What do I do???

---

### Post by mcneely.mike on 2006-08-16
wow! ummmm.  can you apt-get install kde instead?

---

### Post by xpod on 2006-08-16
> I want to install ubuntu, kubuntu and edubuntu on the same pc, same partition

I could be wrong(usually am)but would you not NEED to create 3 separate partitions if it`s 3 different os`s

I know you can use the different desktop environments on the one sys BUT im not sure if thats the same thing.......

Good to know for sure cause i passed on the idea of the dual Gnome/kde thing as i seen loads of people with probs.

---

### Post by anaconda on 2006-08-16
the CD:s are meant for installing to their own partitions..

If I understand correctly, you want to install KDE-, XFCE- and edubuntu-desktops to your existing ubuntu installation?

I dont know, but I think that xubuntu installation CD doesn't have xubuntu-desktop package, and kubuntu-CD doesn't have kubuntu-desktop package... 

because for example if you install xubuntu-desktop to your ubuntu you don't get FULL xubuntu, you just get XFCE windowmanager in addition to your existing GNOME.

You should go to a machine with internet connection, download the packkages you want (eg. xubuntu-desktop) ant burn THEM to a CD ant try the same. Or you could install the different variations of ubuntu to different partitions..

---

### Post by aysiu on 2006-08-16
You can install these from CDs only if they are the **Alternate CDs**. The **Desktop CDs**' repositories do not have the full desktop environment.

---

### Post by mayank.abhishek on 2006-08-18
> **mcneely.mike said:**
> wow! ummmm.  can you apt-get install kde instead?

No, that dosen't work either!

> **xpod said:**
> I could be wrong(usually am)but would you not NEED to create 3 separate partitions if it`s 3 different os`s

I know you can use the different desktop environments on the one sys BUT im not sure if thats the same thing.......

Good to know for sure cause i passed on the idea of the dual Gnome/kde thing as i seen loads of people with probs.

No, I want them on one installation.

](*,) Help!

---

### Post by jrjr on 2006-08-18
.

---

### Post by aysiu on 2006-08-18
> **mayank.abhishek said:**
> No, that dosen't work either! Actually, that *does* work, except that you need either the **Alternate CDs** or an internet connection.

You cannot *apt-get* or *aptitude* install desktop environments off the **Desktop CDs**.

---

