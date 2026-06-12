---
title: "GParted corrupted my home partition, is there anyway to save my data?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-02-13
When I installed Ubuntu, I accidentally made my boot partition 50 GB too big.  I just noticed it, and so I booted GParted to move the space from my boot to home partition.  I left it on when I went to school, and I just came back and it says that the filesystem for my home partition is undefined, and has an explanation point next to it.  Ubuntu won't boot, so is there anyway to save my files before I reformat?

Thanks.

---

### Post by ola on 2008-02-13
If you try to boot up from an (Ubuntu) Live CD and try to mount your partition with mount /dev/hda1 (or whatever your partition is) /mnt/hda1 you might be able to mount it.

Apart from that I have no other ideas. Good luck and hope you save the files.

---

### Post by Yes on 2008-02-13
How should I mount it?  I tried mount /dev/sda7 /mnt/sda7 and it gave me an error, "mount: mount point /mnt/sda7 does not exist".  I got the sda7 from fdsik -l.

Thanks.

---

### Post by Yes on 2008-02-13
Anyone?

---

### Post by Sinkingships7 on 2008-02-13
try just sda, or sda1

---

### Post by Herman on 2008-02-13
If the file system is undefined it will probably be impossible to mount it.

The way to mount a file system normally would be to make a mount point for it first, (an empty folder somewhere, usually in the /mnt or /media directory, but it could be anywhere), like this,
```
sudo mkdir /media/home_partition
```'home_partition' is just a name for the new folder that I made up, you can make up any name you like.
We'll use that folder for our 'mount point'.

Then, you can mount it, like this,
```
sudo mount -t ext3 /dev/sda7 /media/home_partition
```The 'sudo' part of that command tells Ubuntu you are the system admin, authorized to do such things, and it will ask you for your password to prove it.
The -t ext3 part of the command tells Ubuntu what kind of file ssytem it is you want to mount, it could be vfat, or reiserfs, or ntfs or anything.
The /dev/sda7 part tells Ubuntu what partition you're trying to mount. You probably know that from looking in GParted.
And /media/home_partition is the mount point you just made.

As I already said, I don't think you'll be able to mount it now anyway, because if it's true that the file system is undefined, then there's no file system to mount.
You can try again to see anyway, but I doubt if it will work.

What I would do in that situation would be to use TestDisk to re-write the partition table the way it was before. Here is my web page about how to use TestDisk, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html")  it has helped a few others in the past, I hope it's simple enough for anyone to understand. Just take your time and take a look at all that first and try to read as much as you can. Good luck with it.
Regards, Herman :)

---

### Post by Yes on 2008-02-13
What would reverting it do, just put it back to the way it was before I started moving things around?

---

### Post by macogw on 2008-02-13
> **Yes said:**
> What would reverting it do, just put it back to the way it was before I started moving things around?

It'd probably make things worse.  Avoid messing with the partition table at all until either you get that stuff off and backed up elsewhere or you give up.

---

### Post by Herman on 2008-02-13
Yes, if you make the right choices in TestDisk, you'll be able to restore your partition table and file systems to the what they were like before you tried to resize your boot partition from 50GB and resize your /home partition.

At least that will give you access to all your files again.
You'll still probably want to try the resize operation again. Hopefully you'll be luckier next time and everything will go as planned.

Regards, Herman :)

---

### Post by Yes on 2008-02-13
And so if I can't back my stuff up, I should just format/reinstall instead of doing what Herman said?

Thanks.

---

### Post by Herman on 2008-02-13
:) Yes, are there any other partitions on this hard disk that might contain important files besides your Ubuntu /home partition? 

I was assuming the Ubuntu partition was the only partition with important data, and at the moment it doesn't seem to be mountable without using TestDisk to recover the file system first.

Regards, Herman :)

---

### Post by Yes on 2008-02-13
No, but if there's not much of a chance that it'll work I'd rather not have to install Windows again.

---

### Post by Herman on 2008-02-13
TestDisk has helped other people get back all their data a few times in the past that I know of.
There's always a chance that something might not work, especially if it's the first time you use something.
That's the reason why I made a web page to illustrate how TestDisk can be used, so people can see what it's like before they try it themselves. 
If you do decide to use it, read all you can first, and if possible, try it out first on a old hard disk that has information on it you don't care about.
TestDisk is quite simple to use once you get the hang of it.

In any case, you should always make backups of all your data anyway.

I guess it's up to you to decide whether the data you hope to recover is worth the risk to your Windows installation or not. Only you know what you had in there. If there isn't very much data and none of it is important at all then maybe just re-instsalling Ubuntu over the top of it really would be the best decision. 
I would think it over for a while first maybe, there's no hurry.

Regards, Herman :)

---

### Post by maestrobwh1 on 2008-02-13
You could also try using a knoppix live CD.  I have had that work with <damaged> data before.  If it reads/mounts (it puts device icons on your desktop and so what ever is detected might mount).  You could also run fsck using knoppix if you can get it to identify the file system in question.

Testdisk saved me once as well.  BEFORE doing this, do this

Google clonezilla live, download the iso file, burn it to disk.  Boot from the CD and it will help you clone your working partitions to an image file (free and it ALWAYS works)  You need a working partition/disk/usb device that can hold your data.  It does compress your data so if your installation is sat 8 GB, it might only need 6 GB space.  

This way if you crash anything that is working, you can restore it.  If you have two working partitions with enough room, you can mount one to save the other one then start the program over and mount the other partition and save the first.

---

### Post by Yes on 2008-02-14
Ok, I was reading the first guide linked to on your site, Herman, and it says to install "gddrescue".  But when I do sudo apt-get install gddrescue, it says that it can't find it.  I have universe repos enabled, do you have any ideas what to do?

---

### Post by Herman on 2008-02-14
sudo apt-get update?
```
sudo apt-get update
``````
sudo apt-get gddrescue
```If it still doesn't work, check your /etc/apt/sources.list again, you should be able to download it if you have the normal repositories enabled.

DO you edit your /etc/apt/sources.list with gedit text editor or do you do it the GUI way? ('System'-->'Administration'-->'Software Sources').
If you're doing it the GUI way try 
```
gksudo gedit /etc/apt/sources.lst
```Remove (delete) an single hash marks to uncomment more repositories.
[    Enable Standard Repositories]("http://users.bigpond.net.au/hermanzone/p5.htm#Enable_Standard_Repositories")

If you're doing it from a Live CD your /etc/apt/sources.lst might be different. I hope gddrescue is available to the Live CD operating system. It should be,

Regards, Herman :)

---

### Post by Yes on 2008-02-14
Great, I just had to run sudo apt-get update.  I'll try ddrescue and if that doesn't work I'll try TeskDisk.

Thanks for all your help, it's much appreciated :)

---

### Post by bren on 2008-02-14
> TestDisk has helped other people get back all their data a few times in the past that I know of.
There's always a chance that something might not work, especially if it's the first time you use something.
That's the reason why I made a web page to illustrate how TestDisk can be used, so people can see what it's like before they try it themselves.
If you do decide to use it, read all you can first, and if possible, try it out first on a old hard disk that has information on it you don't care about.
TestDisk is quite simple to use once you get the hang of it.

+1 testdisk saved my data more than once!

bren

---

### Post by Yes on 2008-02-15
Ok, ddrescue didn't work but TesdtDisk did!  I'm currently backing up all my files to another hard drive and then I'll reinstall Ubuntu.  

Thanks!

---

### Post by Herman on 2008-02-15
:cool: Cool!

---

