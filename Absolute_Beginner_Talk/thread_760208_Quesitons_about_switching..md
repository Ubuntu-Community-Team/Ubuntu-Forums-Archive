---
title: "Quesitons about switching."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by decoy26517 on 2008-04-19
Hi there!
I had a few questions about installing a dualboot system and I was wondering if I could get some help.

First, a bit of background. I installed ubuntu on an older system of mine as a test dual boot system just to see how it ran. While I was very happy with it, it ran horribly compared to widows XP on the same system. I mainly think this was because I didn't plan ahead and had no idea what I was doing. Now I'm trying the switch again (½ switch I guess...) and installing ubuntu on my newer system along with Windows Vista. 

Current systems hardware: 
Intel Core2 Duo 6750 OC 3.0ghz
Gefore 8800 GTS 
4GB DDR2 800

Now onto my questions! 
1)Ubuntu, Xubuntu or Kubuntu. From what I understand Xubuntu is the fastest of the 3 (uses the fewest resources.)  But which is better? What are the advantages/disadvantages of them? _Which is easier to learn?_
2)Partitioning; this is what I think killed me the last time I tried to install ubuntu. Ubuntu can READ from the NTFS file format but not write to it correct?  
3)Ubuntu has to be installed on the ext3 file system; do all of your applications/files that you use with Ubuntu have to be in the ext3 partition as well? 
4)I have 2 hard drives, I am considering having the main drive (C:\) as my windows OS partition, and having Ubuntu on my 2nd drive (E:\). Will this cause any issues? Will the Windows OS be able to talk to the E: Drive and vice versa? Or would it be easier or better to have both OS's on the C: drive and the applications and files on the E: drive? Or does it even matter? 
5)Is it easier to have the whole HD as ext3 and install Vista on that or have the whole drive as NTFS and install Ubuntu just as on the ext3 partition? 
6)I'm considering installing either 8.04 or 7.10, should I go ahead and try the beta 8.04 version or wait until it's final release? 


I'm sure I'll find some more questions as time progresses, if there are any other tip you guys can throw my way I'd appreciate it as I do a bit more research.

---

### Post by LaRoza on 2008-04-19
> **decoy26517 said:**
> 
Current systems hardware: 
Intel Core2 Duo 6750 OC 3.0ghz
Gefore 8800 GTS 
4GB DDR2 800

1)Ubuntu, Xubuntu or Kubuntu. From what I understand Xubuntu is the fastest of the 3 (uses the fewest resources.)  But which is better? What are the advantages/disadvantages of them? _Which is easier to learn?_
2)Partitioning; this is what I think killed me the last time I tried to install ubuntu. Ubuntu can READ from the NTFS file format but not write to it correct?  
3)Ubuntu has to be installed on the ext3 file system; do all of your applications/files that you use with Ubuntu have to be in the ext3 partition as well? 
4)I have 2 hard drives, I am considering having the main drive (C:\) as my windows OS partition, and having Ubuntu on my 2nd drive (E:\). Will this cause any issues? Will the Windows OS be able to talk to the E: Drive and vice versa? Or would it be easier or better to have both OS's on the C: drive and the applications and files on the E: drive? Or does it even matter? 
5)Is it easier to have the whole HD as ext3 and install Vista on that or have the whole drive as NTFS and install Ubuntu just as on the ext3 partition? 
6)I'm considering installing either 8.04 or 7.10, should I go ahead and try the beta 8.04 version or wait until it's final release? 


Hardware will work.

1. The speed differences are minor in those three. Ubuntu is the most commonly used. If you want the other desktop environments, you can install them in Ubuntu (same with all the others) without touching anything.

2. Ubuntu can now read and write to NTFS with no problems.

3. Ubuntu can't be installed to an NTFS or FAT32 partition, ext3 is the most popular but others work also. Other files can be on other partitions, disks of another format.

4. It doesn't matter. I have Windows and Ubuntu on the same disk, and reserve my other disk for storing files. I keep the Windows and Ubuntu partitions small (30 GB) and use the rest of the disk for storing files as well.

5. Windows needs NTFS. Install Windows first (if it isn't already installed). Use Ubuntu to resize the Windows partition.

6. 8.04 seems to work well know. Get the RC if you use it.

---

### Post by GuitarRocker2562 on 2008-04-19
That guy summed it up. But seriosuly back up yor data before installing, and read a guide on installing a dual-boot, no offense, but noobs have a higher risk of losing their data. 8.04 will work fine. All of them take some time to learn, but I would highly suggest ubuntu, it has more support, it more up to date, and I think it is easier to use. Good luck!

---

### Post by Diabolis on 2008-04-19
1) The difference between them is the graphic user interface(desktop environment).
     In the inside they are pretty much the same.

2) Linux does have a bit of trouble with ntfs. There is already support for it and is supposed to be good, but last time I checked It wasn't too good.
However this should not be a problem. You can make 3 partitions 
1.- ntfs for vista
2.- ext3 for ubuntu
3.- fat32 for file storage

Both linux and windows can write/read to a fat files system.

3) no

4) It doesn't matter which drive you use for your partitions, all what matters are file systems.

5) each partition is the with its own file system. So a hard drive can have many partitions and every partition with a different file system.

6) 8.04 could have some bugs, but I have heard that it is better than the current release ever was. If you have a big hard drive, install both lol.

---

### Post by frup on 2008-04-19
> **decoy26517 said:**
> 
Now onto my questions! 
1)Ubuntu, Xubuntu or Kubuntu. From what I understand Xubuntu is the fastest of the 3 (uses the fewest resources.)  But which is better? What are the advantages/disadvantages of them? _Which is easier to learn?_

Personally I would say go with Ubuntu. It has the most support and the most features. This is a personal opinion. If you start with Ubuntu you can install XFCE/KDE etc as well and try all 3 and choose which one you like best
> **decoy26517 said:**
>  
2)Partitioning; this is what I think killed me the last time I tried to install ubuntu. Ubuntu can READ from the NTFS file format but not write to it correct? 

That has all been fixed. Installation is very simple and the CD will do the partitioning for you, you just choose how much space you want to give to windows and ubuntu. Ubuntu can now read and write to NTFS by default
> **decoy26517 said:**
>  
3)Ubuntu has to be installed on the ext3 file system; do all of your applications/files that you use with Ubuntu have to be in the ext3 partition as well? 

Files do not have to be, it's easiest if you have most things set as default with maybe a seperate home. If you want to change this you probably want to search for some detailed tutorials
> **decoy26517 said:**
> 
4)I have 2 hard drives, I am considering having the main drive (C:\) as my windows OS partition, and having Ubuntu on my 2nd drive (E:\). Will this cause any issues? Will the Windows OS be able to talk to the E: Drive and vice versa? Or would it be easier or better to have both OS's on the C: drive and the applications and files on the E: drive? Or does it even matter? 

That's completely up to you, it really shouldn't matter as far as I know. The one thing you will have to do though install an Ext3 driver on windows to see the Ubuntu partition
> **decoy26517 said:**
> 
5)Is it easier to have the whole HD as ext3 and install Vista on that or have the whole drive as NTFS and install Ubuntu just as on the ext3 partition? 

Vista can not install on ext3. Ubuntu can't install on NTFS. Install Vista first if you dual boot and le Ubuntu sort out it's magic.
> **decoy26517 said:**
> 
6)I'm considering installing either 8.04 or 7.10, should I go ahead and try the beta 8.04 version or wait until it's final release? 

8.04 is in release candidate, it really wouldn't hurt to install. I wouldn't bother going with 7.10... you'd be better off waiting the 4 days until the final is released if that matters to you (release candidate has barely any changes, if any to final)

Cheers and good luck :)

---

### Post by dark_harmonics on 2008-04-19
I disagree. Support for NTFS has been working fine for me for more than 8 months (since i switched). I have another NTFS drive in my computer that i just never bothered to convert. The headache i noticed with it is that it doesnt have permissions like ext3 does. We still use it every day (its my music and pictures storage drive) without any errors.

---

### Post by jesusfreak107 on 2008-04-19
Answers:
1) yes, Xubuntu is fastest, but with your specs, you will not see any difference at all, and Ubuntu has a lot more functionality.  Use normal Ubuntu.  Kubuntu is made to look good, as far as I understand, and resembles windows more so than the other versions.  Ubuntu would be easiest to learn. 

2)As LaRoza pointed out, Ubuntu can read and write to NTFS, but not install on, and NTFS is needed to install windows on. 

3)yes, ext3 is needed to install Ubuntu, but I do not know if you can run applications on a NTFS file system, I have never tried it, it is a Big Red Button that I am not willing to push right now. 

4)No, Windows will not be able to communicate with the Ubuntu drive, at least not without any additional software, and I do not know if any even exists that will do that.

5)have one drive/partition NTFS, w/windows, and one ext3 drive/partition with Ubuntu.  as for whether to use a drive or a partition for those OSes, it is entirely dependent on your preferences.  

6)Try 7.10.  I do not know about 8.04, but it is still a beta right now, and I have heard about quite a bit of problems, but 7.10 is stable, and works fine, and, hey, you can always upgrade.

Hope I helped!
:guitar::guitar::guitar:

---

### Post by SlappyPappy on 2008-04-19
I'll second no problems with NTFS so far. I've only been up a couple of weeks but I've been moving a lot of files around with an external hard drive formatted for NTFS. So far, hasn't missed a beat.

YMMV of course.

---

### Post by decoy26517 on 2008-04-19
Holy cow that's a lot of quick replies!

Thanks for the info everybody. I'm currently backing up everything that matters and going to defrag both drives tonight. One more question: Besides install/updating drivers, setting the resolution etc... are there any performance settings or installs that I need to do once I've started the OS? 

Thanks again!

---

### Post by jesusfreak107 on 2008-04-19
okay, you are *obviously* confused.  you are running a *good* computer, let me tell you!  with a dual core proccesor, and 4GB of RAM, and Ubuntu 7.10, you will NEVER have to worry about speed issues.  just throw that our of your mind!  unless you are running Crysis under Wine or some other ridiculously demanding game, you will never have a problem!

---

### Post by Diabolis on 2008-04-19
Yeah your pc is really fast, specially that video card of yours. You could load all the eye candy you can find in the internet without problem.

---

### Post by decoy26517 on 2008-04-19
> **jesusfreak107 said:**
> okay, you are *obviously* confused.  you are running a *good* computer, let me tell you!  with a dual core proccesor, and 4GB of RAM, and Ubuntu 7.10, you will NEVER have to worry about speed issues.  just throw that our of your mind!  unless you are running Crysis under Wine or some other ridiculously demanding game, you will never have a problem!


Well again, remember my first install I did have performance issues. I mainly contribute that to me not knowing what I was doing :-P But this time I want to make sure that I get all my bases covered before taking the plunge. I doubt I'll be running Crysis or anything of that sort.

---

### Post by barbedsaber on 2008-04-20
[try this guide]("http://www.psychocats.net/ubuntu/partitioning")

for planing partitions.

Its not mine, so if it works, you cant thank me for writing it, and if it doesn't, you cant blame me, i'm just the messenger.

---

### Post by hiloguy on 2008-04-20
I'm happily running 7.04 and Photoshop and other Adobe programs are installed and running sweetly.  This is on a laptop that started out as my new adventure into Linux and so far, I love it.

So now I'm thinking of starting over with a dual-boot (XP-Pro) installation and moving up to 8.04 in the process.  My questions:  Will I still be able to run Photoshop under 8.04 or are there changes that would make that less likely?  Is 8.04 a real advancement over 7.04, or should I just stay where I am?  I've read on this forum several times that if you have 7.04 configured and running glitch-free, the move to 7.10 is not recommended, but how about to 8.04?

My reason for the dual boot is just for those occasions where I need to do something that for now I cannot do under Linux.  

I know it's kinda like starting all over again configuring everything, but it should be easier this time!

Thanks for any thoughts on this . . .

---

