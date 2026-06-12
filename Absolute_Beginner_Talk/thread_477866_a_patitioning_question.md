---
title: "a patitioning question"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-06-18
i thought i'd try a dual boot edgy/winxp system with:

winxp os 20gb ntfs
ubuntu os 20gb ext3
swap 2gb
other left over fat32?

should the other part be fat 32 to install all my programs & files/ not 100% sure how all that should work. would both linux & windows programs go in 'other' or what?

hope i make some sense, have never done anything like this before & thought it'd be interesting to try. :P have searched around but cant seem to find real explanation on the whys & whats.

---

### Post by raja on 2007-06-18
You cannot share programs between windows and Ubuntu.
You can set up a shared partition for your data though - photos, music and documents - so that both OS can share them. The simplest way to do it is as a FAT partition. But NTFS with ntfs-3g in Ubuntu to allow write-access is also OK.
You should have a separate /home partition for Ubuntu (Maybe about 6 GB for / and remaining for /home) - it has some advantages that you will appreciate later.
Unless it is a laptop that you need to hibernate, I dont think you need that much RAM.

---

### Post by bodhi.zazen on 2007-06-18
First, how big is your hard drive.

Second 20 Gb is on the small side for windows.

Third, you will not mix and match how and where you install program. 

Windows : Windows likes to install programs to C:\ Some stuff can be installed to another partition (E:\ ?? ) but some stuff will not.

Linux : The Linux file system is very different. Programs are not installed into a c:\Programs directory, but in /bin /sbin /usr/bin etc

Reference :  	[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

So, I would advise :

c:\ 30 =40 Gb (if you can spare the space)

Ubuntu 10-15 Gb (can go as low as 5, but you would run out of space very soon)

Swap = Ram X2, max 1 Gb, or max = ram if > 1 Gb ram and you want to hibernate.

Rest = data partition. I like ext3 as a shared partition. You can mount ntfs with Ubuntu and Ext2/3 with windows.

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by lunaz on 2007-06-18
i have an 80 gb hd. i forgot to mention :P
ty for the clarification. :)

---

### Post by Sceiron on 2008-02-20
> **bodhi.zazen said:**
> 
Reference :  	[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)


This was a very good reference :)

In the first sticky on Absolute beginner talk forum there is a thread saying:
> 9) Have seperated partitions.
A good idea is to have / (root), /home and /boot
Read more...
 And it has a link to a guide of partitioning. But i wonder:
How do i create a partition for "/home"?
And if i do so, could i then format/reinstall ubuntu without loosing data that is in this "home-partition"?

Best Regards
Sceiron

---

### Post by indytim on 2008-02-20
> How do i create a partition for "/home"?
And if i do so, could i then format/reinstall ubuntu without loosing data that is in this "home-partition"?

If you are doing a fresh install, for a dedicated /home, my recommendation is to pre-configure an ext3 partition sized to where you want your /home to be at.  When it comes time to install, do the manual partition option and identify the partition referenced above as your '/home' partition.

One of the advantages of having a dedicated /home partition is that your settings will be saved if you disrupt your ops partition (like installing a new version of the ops).  This applies as long as you do the manual configure of your partitions at install.

If you are interested in going to a dedicated GRUB partition, see the link in my signature.

IndyTim

---

### Post by Forrest Gumpp on 2008-02-20
Have a look at Herman's Illustrated Dual Boot Site:  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Approximately two screens down this page are three install guides.  It sounds like you will be best helped by the third one titled 'separate home'.  Click on the title link.

The guide is for Feisty and the Alternate CD, but should still help you.

aysiu's Ubuntu Linux Resources is equally valuable if you plan to use the Desktop CD.  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Specifically, within aysiu's page:  [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)  and  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by housam on 2008-02-20
> **Sceiron said:**
> 
How do i create a partition for "/home"?
And if i do so, could i then format/reinstall ubuntu without loosing data that is in this "home-partition"?
Sceiron
Look at this link [[COLOR="Red"]http://www.psychocats.net/ubuntu/separatehome[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by louieb on 2008-02-20
Just a quick note on disk space for Win/XP.  
I have XP Home without a lot of extra programs installed on a 8GB drive. Its about 55% used. I use it for my print server.

My laptop has XP Pro, office 2003, and few smaller programs in a 14GB partition. Its about 55% used.   

As far as my Ubuntu install:  7-10GB for / (root), a small /home 2-4GB and the rest of the drive space for a data partition. Since I normally boot to Ubuntu my data partition is ext3. If I used XP more I would probably make it NTFS.    

Lots of good points and links by the other posters. You'll just have to play around with it and see what works for you. Good luck.

---

### Post by bodhi.zazen on 2008-02-20
> **Sceiron said:**
> This was a very good reference :)

In the first sticky on Absolute beginner talk forum there is a thread saying:

 And it has a link to a guide of partitioning. But i wonder:
How do i create a partition for "/home"?
And if i do so, could i then format/reinstall ubuntu without loosing data that is in this "home-partition"?

Best Regards
Sceiron

You do not need to re-install, you can move home:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

To manage partitions I advise you use Gparted from a live CD

Gparted Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

