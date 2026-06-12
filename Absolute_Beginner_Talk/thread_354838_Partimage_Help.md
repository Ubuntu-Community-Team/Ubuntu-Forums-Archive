---
title: "Partimage Help"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by shashank on 2007-02-06
they say that the partition we want to bacup should be unmounted.
So do i have to type some command or is it that its not mounted frm the begning only?

another question is that can i save an image in NTFS file system,
and if i can make a fat32 partition and save all my images there thn i can i restore frm it?



i HAVE READ ABOUT NORTON GHOST 10 .can IT help?
basicaly i want to backup two partition (ntfs loaded xp,ext3 loaded ubuntu)

---

### Post by Brunellus on 2007-02-06
thread title changed for legibility.  I take a dim view of cLeVerLY cApItalIzEd titles, and an even dimmer view of 1337 5p33k.

What, exactly is the problem?

---

### Post by click4851 on 2007-02-06
someone else please chime in if I'm wrong here, but if you want to backup the partition you booted the computer with you need to unmount that first. Of course if you unmount that how do you run the computer to run partimage? I ended up using Gparted Live CD to boot the computer and then all harddrives are unmounted because the computer booted from the Live CD. I bet partimage has a Live CD setup or something similar, somewhere that would do the same. I was stuck because the partition choices I made at the initial install. i would start with the partimage website or docs and go from there.

P.S. I can't speak for partimage and NTFS, but Gparted handles NTFS just fine.

---

### Post by shashank on 2007-02-06
look i just tried to use partimage . iam not quite familiar at it .
i managed to make backup images on a fat32 but after that it wont recover.it say file not found at specified place!.

i entered after mounting fat32 at /backup and image file was image1.000

/backup/image.000 and it wont work it comes out of partimage!

---

### Post by shashank on 2007-02-06
Yes I Used Gparted Live Cd But It Would Just Come Out Of Gparted Program At Recovering When I Specify File Image Name!

---

### Post by shashank on 2007-02-06
Soory I Meant Partimage Live Cd !

---

### Post by shashank on 2007-02-06
I Thoght Gparted Was Just For Reparttining .is It Also For Back Up?

---

### Post by Brunellus on 2007-02-06
please refrain from bumping unnecessarily.  If you need *really urgent* help, try IRC:  #ubuntu at irc.freenode.net

---

### Post by shashank on 2007-02-06
[http://irc.freenode.net/](http://irc.freenode.net/)

IS NOT WORKING?

---

### Post by click4851 on 2007-02-06
I hope thats a typo in the the file name of your post, because they are different. I don't have much experience with partimage as I said, but I don' think you need to mount anything once your running the LiveCD enviroment. I'd have to read the docs before I could walk you through it. I would review the docs and just go slow and make sure the exact path name is entered, just one character off will bollocks the whole deal (no file found).

---

### Post by click4851 on 2007-02-06
yes Gparted will copy one partition on one drive to another, having said that I don't think it makes images like partimage.

---

### Post by Frank Golden on 2007-02-06
Partimage is a Linux analog to Ghost. In my humgle opinion it is way better.
See this for info on using the version of partimage on the System Recovery CD.

[http://www.ubuntuforums.org/showthread.php?t=287522](http://www.ubuntuforums.org/showthread.php?t=287522) this is a wiki adapted by a kind member from a how to posted by myself earlier.

Below is the original how to.


[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)

I use partimage all the time to make backup images of my Linux partitions.
I find the best results come from savind the image file to a Fat32 partition on the same drive as the Linux partition I am backing up.
The whole process of backing up (imaging) a ~4GB used Linux partition (the process only makes an image from the used space on the partition that the Linux install is on). So where the total partition may be for instance 10GB, if the used space is only 3-4GB
that will be the size of the saved partimage image. The thing to remember however
is that if the initial size of the whole partition is say 10GB the size of the partition to restore to must be 10GB or greater. This is regardless of whether the image size is is ~4GB as used in the example above.

Once you have used partimage a few times it will become second nature.
Using it to create and store an image to a Fat32 storage partition on the same drive
takes me about 10 minutes at gzip compression. This results in a file size of about 1.65GB
for a 4GB initial used space.

There is a feature in the program to span several images together if the resulting
image will be greater than 4GB, which is the limit imposed by the Fat32 file system.

Of course you could create a ext3 partition instead of a Fat32 one for storage an get around this "limitation".

The reason I use Fat32 is I dual boot XP and a couple of Linux distros (Ubuntu and PCLinuxOS) and I use the Fat32 partition for data storage across platforms.

I presently have the latest updated and stable images of my Ubuntu and PCLinuxOS
installs imaged and available on that Fat32 partition. If I hose either install I can restore
using partimage either distro in about 10 minutes.

I use it all the time as I experiment with settings and seem to break Linux regularly. LOL.

Every time a do a major update or add software or make a major config change, I first prove it out and then make a new image replacing the old one.

I think you are supposed to be able to image and restore a NTFS volume (XP for instance)
using the latest version with the latest SystemRescueCD. But I have no interest
in that as I use Ghost 9 in XP for that. Check the documentation in the partimage website.
(google it).

Once you get adept at using partimage you will wonder how you ever got along without it.
Really!!!

---

### Post by Brunellus on 2007-02-07
> **shashank said:**
> [http://irc.freenode.net/](http://irc.freenode.net/)

IS NOT WORKING?
irc is a chat protocol.  use Xchat, irssi, gaim or kopete to connect to irc.freenode.net

---

### Post by rickyrockrat on 2007-11-05
I've written a wrapper around partimage.  You can see it here and try it out:

[http://www.partimage.org/forums/viewtopic.php?p=1762](http://www.partimage.org/forums/viewtopic.php?p=1762)

Its under the GPL. I wrote the wrapper because I couldn't find ANY whole-disk backup solution that just copied used blocks.

The wrapper does auto-zero and will verify (with MD5 sums), but verify takes a LONG time.

Enjoy.

---

