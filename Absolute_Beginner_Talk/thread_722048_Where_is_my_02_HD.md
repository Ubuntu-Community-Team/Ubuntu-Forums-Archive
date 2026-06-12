---
title: "Where is my 02 HD??"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by roninjapan on 2008-03-12
HI i just change to Linus and cant understund this please help.

before i use linux i have windows with 02 Hard Disks.....(C: and D: d full of data) now i install UBUNTU and when search i get this

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18909   151886511   83  Linux
/dev/sda2           18910       19452     4361647+   5  Extended
/dev/sda5           18910       19452     4361616   82  Linux swap / Solaris


where is d:?how can acess D:...can change letters as was in windows...C: and D...

i read something about MOUNT the HD but i can understund.anyone can talk to me in easy plain no geek words please.

thanks to all read this.

---

### Post by Fred_E _krugar on 2008-03-12
well you second disk is probably formated in ntfs which not a normal breed for linux. 
Linux is starting to get support for it though I think it is called ntfs-g or something like that. 


You could try Gparted to at least see if it can see it.

---

### Post by ad_267 on 2008-03-12
If you're using 7.10 Gutsy Gibbon then it should be able to see ntfs drives automatically. What version of Ubuntu are you using?

---

### Post by Whiffle on 2008-03-12
Which command did you use to get that list?

---

### Post by roninjapan on 2008-03-12
my ubuntu is last version.7.10


command i used is 
sudo fdisk -l


i installed GPARTED and shows....



Any idea to acess the old HD that i have as D: full of precious files... :(


thanks 

(Move to Linux was my best shot..linux rocks!)

---

### Post by Whiffle on 2008-03-12
Okay linux doesn't even see your second drive as existing or being connected to your computer.  It doesn't matter what filesystem its using, it would show up in gparted or fdisk -l (don't worry, its not lost).  How is that drive connected to your computer?  Is it connected to an add on card of any kind?  Can we get some more details on your hardware?  The output of "lspci -v" could be helpful.

---

### Post by ad_267 on 2008-03-12
Can you click on the drop down list in the top right of gparted (where it says "/dev/sda (149.01 GiB") and select the other drive?

---

### Post by Fred_E _krugar on 2008-03-12
Did you click the little down arrow in the upper right hand corner of Gparted , I am just checking.

---

### Post by Fred_E _krugar on 2008-03-12
> **ad_267 said:**
> Can you click on the drop down list in the top right of gparted (where it says "/dev/sda (149.01 GiB") and select the other drive? 


Or what he said lol

---

### Post by roninjapan on 2008-03-12
its a INTERNAL drive. 

I add to have extra space....i

AMD Athlon(tm) 64 Processor 3500+
512 KB and some screenshots...

this help??


thanks for take your time to help me.

---

### Post by Whiffle on 2008-03-12
Hmmm.  I see two hard drives listed in that second screen, one of them is a 160GB Seagate (i think this is the one that is showing up in fdisk and gparted), the other is a 20GB Toshiba, like the kind you'd find in the COWON mp3 player listed in the first screenshot.   Is either of those two the drive we're looking for?  Do you have any information about what kind of drive it is?  AT this point I'm really not sure what to do next, but then again its late and I'm tired.

The thought did just cross my mind that the drive is there, but your C: and D: got overwritten.  If thats the case, then you'll want to stop using the computer and find some data recovery software, because the data is probably still there.

---

### Post by roninjapan on 2008-03-12
Sorry did read your post..[COLOR="Red"].not i cant open[/COLOR]...dont show any opetion to choose another HD.

"Can you click on the drop down list in the top right of gparted (where it says "/dev/sda (149.01 GiB") and select the other drive?"

---

### Post by roninjapan on 2008-03-12
> **Whiffle said:**
> Hmmm.  I see two hard drives listed in that second screen, one of them is a 160GB Seagate (i think this is the one that is showing up in fdisk and gparted), the other is a 20GB Toshiba, like the kind you'd find in the COWON mp3 player listed in the first screenshot.   Is either of those two the drive we're looking for?  Do you have any information about what kind of drive it is?  AT this point I'm really not sure what to do next, but then again its late and I'm tired.

The thought did just cross my mind that the drive is there, but your C: and D: got overwritten.  If thats the case, then you'll want to stop using the computer and find some data recovery software, because the data is probably still there.


Sorry.....when i take picture i forgot i have conected my media player...(dumb)....forget the Cowon HD...this i out.

my problem is D:....i believe 160    is the old C:...(or D:) and one of them is missing.seams just show one HD...the other is invisible.terrible.!!i gonna get crazy.

---

### Post by tubasoldier on 2008-03-12
First off I highly doubt your data was overwritten, uless thats where you installed Ubuntu. 

let's start with why your D: drive, as you call it, does not show up. In Linux we don't give hardware a name, we give it a place. Everything in Linux is a file, including all hardware. More than likely your hard drive resides quite safely on /dev/sdb.

I would try mounting this drive first. But because everything is a file, you first need a place to put it. Open up a terminal and type or copy/paste the following:

```
sudo mkdir /mnt/D
```

Then try mounting the disk by typing or copy/paste the following into the terminal:

```
sudo mount /dev/sdb /mnt/D
```

Then you can browse to that location and see your data. You could also create a directory in your own /home directory to mount it in (eg. /home/D). /mnt is just a unix standard. Basically you create a directory and then mount a disk to that directory. Thus giving it a place, not a name! to unmount it you simply use umount instead of mount.

Good Luck

---

### Post by roninjapan on 2008-03-12
xxxx

---

### Post by tubasoldier on 2008-03-12
> **roninjapan said:**
> xxxx

HUH? does that mean it worked? Or are you still having trouble?

---

### Post by roninjapan on 2008-03-12
> **tubasoldier said:**
> First off I highly doubt your data was overwritten, uless thats where you installed Ubuntu. 

let's start with why your D: drive, as you call it, does not show up. In Linux we don't give hardware a name, we give it a place. Everything in Linux is a file, including all hardware. More than likely your hard drive resides quite safely on /dev/sdb.

I would try mounting this drive first. But because everything is a file, you first need a place to put it. Open up a terminal and type or copy/paste the following:

```
sudo mkdir /mnt/D
```

Then try mounting the disk by typing or copy/paste the following into the terminal:

```
sudo mount /dev/sdb /mnt/D
```

Then you can browse to that location and see your data. You could also create a directory in your own /home directory to mount it in (eg. /home/D). /mnt is just a unix standard. Basically you create a directory and then mount a disk to that directory. Thus giving it a place, not a name! to unmount it you simply use umount instead of mount.

Good Luck


What i did i creat a folder named D: and after that was in terminal (sudo mkdir /mnt/D) and I get the message..

mkdir: cannot create directory `/mnt/D': File exists


????dont get it

---

### Post by tubasoldier on 2008-03-12
The directory already exists. So all you have to do is mount the drive. Unless it is already mounted there.

---

### Post by roninjapan on 2008-03-12
this is what i get ...when try mount.

sudo mount /dev/sdb /mnt/D
sergio@sergio-desktop:~$ sudo mount /dev/sdb /mnt/D
mount: special device /dev/sdb does not exist

---

### Post by bodhi.zazen on 2008-03-14
> **roninjapan said:**
> this is what i get ...when try mount.

sudo mount /dev/sdb /mnt/D
sergio@sergio-desktop:~$ sudo mount /dev/sdb /mnt/D
mount: special device /dev/sdb does not exist

First, that command will not work. /dev/sdb = entire HD, you need to specify a partition:

```
sudo mount /dev/sdb1 /mnt/D
```

Check out this link for partitioning jargon :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Second, we need to look at your partitions.

Can you post the FULL output of this command ?```
sudo fdisk -l
```

You can also look at these links, we will walk you through them.

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)

---

