---
title: "Is there a utility for ubuntu for copying entire hard disk?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-03-24
I need a utulity that will copy the entire hard disk. I want to move from a small disk to
a larger one without doing a complete reinstall. The utilities available from disk manufacturers will only copy FAT or NTFS.
If anyone know of one that would be great.

---

### Post by bodhi.zazen on 2007-03-24
Always nice to get new hardware ;)

There are several methods.

Perhaps the easiest is gparted. It is on the live CD.

Plug in the new HD, Boot the live CD, fire up gparted

In the gparted menu are copy and paste buttons to copy your partition.

You can then resize the partition or add additional /data /music /home partition(s) on you new HD if you like.

---

### Post by chewearn on 2007-03-24
Like to add that with GParted partition copying, it doesn't copy the mbr.  So if you have grub in the old disk mbr, you need to reinstall grub.

---

### Post by linuxjerk on 2007-03-24
Is there anything for copying on floppy? I'm having a hard time getting the live cd to boot properly. I get the gnome error and my mouse doesn't work in live.

---

### Post by aktiwers on 2007-03-24
You could also make a ghost-image of the partition. Search the forum for howto's.. I have seen there are some here. Or look here:
[http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux](http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux)

---

### Post by linuxjerk on 2007-03-24
You mean to tell me that there is nothing on floppy like the disk makers provide?
I just want to copy directly from one disk to the other. I don't want to use ftp servers and I don't want to repartition.

---

### Post by rbprogrammer on 2007-03-24
i never used it, but you may want to try it out.  something called [partimage]("http://www.partimage.org/Main_Page").... i think its even in the repositories...........

---

### Post by buuntuu! on 2007-03-24
try tar!
point 2.1 of this [howto]("http://www.ubuntuforums.org/showthread.php?t=35087&highlight=tar+backup") wil do for you!

---

### Post by linuxjerk on 2007-03-24
Thanks guys for some great ideas. I guess I'm not going to find a floppy based 
program but some of these may work just as well.

---

### Post by freebird54 on 2007-03-24
Most of the floppy based things don't seem to work too well.  I had 3 of them when backing up my Windows to move it to a larger drive - and ended up having to use GPartEd from the Ubuntu Live CD to get the job done right.  (even my Partition Magic choked on it - though it SAID it had done it).

It is by far the easiest, though NOT the quickest way to move stuff around IMHO.

Good luck!

---

### Post by linuxjerk on 2007-03-29
Could someone fill me in on the usage of parted?
How would I go about copying my entire partition from one hard disk to the other
so the new disk is a bootable duplicate of the original?
thanks

---

### Post by chewearn on 2007-03-29
GParted guide:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
See section "Copying/Moving with GParted".

Restore grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by macogw on 2007-03-29
If you want to do direct block-by-block copying, you can use dd

dd if=/dev/sda1 of=/dev/sdb1

if=disk you copy from
of=disck you copy to

---

### Post by linuxjerk on 2007-03-30
I can't find Gparted on my 6.10 live disk anywhere. It's not in my add/remove list either.
Can someone tell me where to find it?

---

### Post by freebird54 on 2007-03-30
Was it the graphical install?  If so - for SURE it is there.  Open a terminal and type **gparted**...

As for loading it to your system -  System->Adminsitration->Synaptic Package Manager - choose SEARCH once it is up, and type in gparted, mark for installation, click Install...

---

### Post by linuxjerk on 2007-03-31
whan I type on a terminal: gparted I get command not found.
when I search on package manager for gparted it's not found.

Now, parted is there but not gparted.

No reference to gparted on my edgy 6.10 live cd.

---

### Post by chewearn on 2007-03-31
It should be: System > Administration > Gnome Partition Editor

---

### Post by linuxjerk on 2007-03-31
System > Administration > Gnome Partition Editor
That does not exist in that path.

I found reference to Gparted in the Synaptic Package Manager.
Looks like you have to download it from the internet.

But it's not on the live cd. At least I would like someone to show me where!

---

### Post by wthanna on 2007-03-31
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)   

Ghost for Unix is **exactly** what you want... go to the website I just listed... create your floppy disks...  put second drive in pc..... copy info to larger drive.... enjoy... Detailed instructions are on the website provided above

see section 4.4 of the instructions.  This program can upload an entire disk image to an ftp server allowing you to do a "bare metal" restore of a system... regardless of the operating system on the disk..  It can also be used for creating images of disks that are on the same computer (the fastest way you will probably get all the data from your old disk to your new disk.. including the Master Boot Record)

---

### Post by chewearn on 2007-04-01
> **linuxjerk said:**
> System > Administration > Gnome Partition Editor
That does not exist in that path.

I found reference to Gparted in the Synaptic Package Manager.
Looks like you have to download it from the internet.

But it's not on the live cd. At least I would like someone to show me where!

I really don't know why you could not find Gnome Partition Editor in your livecd. Just to be sure, I reload my ubuntu 610 edgy livecd; take a look at the screenshot (sorry for the blurry image, it's my crappy cellphone camera).

---

### Post by linuxjerk on 2007-04-01
Believe me it isn't there. I has to be installed before it shows up.
I'm trying to download it with the synaptic manager but I'm having problems.
I'm also going to look into ghost.
thanks all

---

### Post by linuxjerk on 2007-04-01
I found gparted in the synaptic manager. Every time I try to download it it says failed.
Can someone please check gparted in the synaptic manager and tell me if the website is down or the file is no longer available?
I will try ghost as soon as I can download it.

Also for your info I did try partimage. It fails to compile. I get errors about not finding fortran??????????

---

### Post by linuxjerk on 2007-04-01
This ghost thing is almost 50 megabytes. Sorry I can't do that on dialup.
Has anyone figured out why I can't download gparted with the synaptic manager?
It fails every time. I just tried it again while I was posting this. It says "Could not download all repository indexes"
Guess I'm screwed

---

### Post by linuxjerk on 2007-04-01
How can I get gparted? It's not on my live cd. I can't seem to download it on the synaptic manager.
What's going on here?????

---

### Post by freebird54 on 2007-04-01
Which version of the Live CD do you have?  IF it is the GNOME based one - it HAS to be there, or the installer could not work.  However, if it is the Kubuntu CD, I believe the name of the program is slightly different - just PartEd perhaps?  (haven't been able to find that live CD so far)

There are a number of floppy based (or roll your own cd) copiers out there - easily accessible from Windows as well - though they ALL rely on being the boot media so that the drives are not MOUNTED at the time of the imaging.  Most of these can be found at places such as ZDNet (search for FREE and IMAGE) or at CNet or...

It is the most OS independent type of program out there - some of the ones I have seen boot off the floppy or CD with Linux, some with FreeDOS, some with MS-DOS - you get the idea.  I cannot guarantee that they all work, however :(

Good luck - and take another look on your Live CD - SOMETHING must be there!

---

### Post by linuxjerk on 2007-04-02
Yes I am finding out that this is going to be a read challange. From what I have found the drives you are trying to copy have to be dismounted. So I cannot do this unless I have booted from the live cd. Can someone help me out with gparted?
I will boot from my live cd and try to find gparted. The problem is my mouse doesn't
work with the live cd. Any suggestions here?
There has to be another way to do this. How do you move to a larger hard drive?
Do you reinstall the whole system?? That sounds very time consuming

---

### Post by compmodder26 on 2007-04-02
Are you sure that your LiveCD doesn't have any defects in it?  There is an option for checking for defects in the first menu you see when you boot the CD.

---

### Post by chewearn on 2007-04-02
Have you really look at g4u; it was mentioned in post #19:
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

The download is only 2.7MB (iso zip).  Or two floppies, whichever you prefer.

---

### Post by bodhi.zazen on 2007-04-02
Gparted just released Gparted-clonezilla 

> The GParted LiveCD development team has emailed us to let us know about a new edition of their live CD. Called GParted-Clonezilla, this product is designed to help users with backing up their entire hard disks (not just individual partitions). It supports all major file systems, including ext2, ext3, ReiserFS, JFS, XFS, FAT and NTFS.

Download page : [http://gparted.free.fr/GParted-Clonezilla/](http://gparted.free.fr/GParted-Clonezilla/)

---

### Post by linuxjerk on 2007-04-02
There isn't anything wrong with my cd. I did run the checksum test.
I must have been looking at a larger version of ghost.
I'm downloading the floppies now. I'll let you know.

---

### Post by linuxjerk on 2007-04-02
That clonezilla sounds good except it would probably take me a day to download with dialup.

---

### Post by linuxjerk on 2007-04-02
Just got G4U working. Tested it on some small 6g disks first. Pretty quick but it looks like it copies the entire disk even if no data is there. Took about 15 for the 6g. Now I'm trying 40g disks. You can calculate the time on those. At least I can do it now.
thanks guys.

---

### Post by linuxjerk on 2007-04-02
Well it turns out I was unable to copy the 40g drive using G4U. I got some unrecoverable errors at about 25g. I tried 2 different 40g drives and got similar errors at about the same point. Hard to believe that the 2 drives would be bad at the same place.
Even though it copied nearly 25g the drive would not boot. I guess there is a lot I need to learn about linux.

Too bad G4U has to copy everything, even the empty spaces.

I was able to do a new install on one of the drives that would not copy. I haven't tried the other yet.

I would like to know what kind of success others have had with this utility.

---

### Post by ipsi on 2007-05-07
That's pretty rough dude, I gotta say. Did you ever manage to get it sorted?

Anyway, I've got a kinda related question about this: I assume there is hardware out there that will allow me to connect an internal hard drive to the computer via USB or something? I've currently got a PC with room for only one HD, and I'd like to install another, bigger one. And I'd like to use gparted to copy the entire thing across. I'm not worried about speed (so it can go through USB if it must), I just want to be able to do it. Any suggestions from anyone? Oh, and cheap is good. :)

Thanks all.

---

