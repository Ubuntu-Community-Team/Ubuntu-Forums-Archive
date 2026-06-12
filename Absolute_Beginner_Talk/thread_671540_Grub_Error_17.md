---
title: "Grub Error 17"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-01-18
I'm having this error, how can I fix it?

---

### Post by Kingsley on 2008-01-18
This thread should have the answers to your problem:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by -gabe-noob- on 2008-01-18
K I'll take a look at that, thanks

---

### Post by -gabe-noob- on 2008-01-18
I can't figure out what he wants me to do in my bios.

I'm not sure but I think its the dell *insert code here* bios type

---

### Post by -gabe-noob- on 2008-01-18
OH COMEON is there an eaisier way to do this!!!!! RAWRRRRRR !!!!


After installing Ubuntu on my hard drive( dual booting with Windows XP) I got the Grub 1.5 Error 17 message. Spent 2 days pulling my hair out trying to figure out why I got the error. Browsed the Ubuntu forums, saw good advice, but nothing help. I was just about to give up on Ubuntu, until I just started messing around with my PC and surprisingly     the error was gone! Here's what I did:


1. Enter BIOS
2. Make sure all HDD's are detected.

* *Take note of (write down) the current settings just in case you need to set things back later**

3. Search for the HDD that has Ubuntu installed and set its MODE to AUTO (not LBA, large, or normal)
4. Also, if you have this option available, set TYPE to USER, but don't change any of the figures that were automatically detected.
5. And you are done!


Just in case this doesn't work, then:
6. Set all drives to TYPE --> USER and MODE --> AUTO (not LBA, large or normal)


I just took the time to post this because of the all the trouble I when through for something so simple to do. I hope that this post helps.....
__________________
Reply With Quote


this is what I'm trying to do now.

---

### Post by -gabe-noob- on 2008-01-18
? please HELP!!!

---

### Post by -gabe-noob- on 2008-01-18
srrsly this AINT 1 bit cool.... Please I need some help!

---

### Post by eolson on 2008-01-18
After a bit of snooping around with Google,  I found this.  You might want to read up on e2fsck before you run it.   Man e2fsck should give you the info on it.

Scoll down to the end

[http://www.linuxforums.org/forum/ubuntu-help/90995-grub-error-17-but-nothings-changed.html](http://www.linuxforums.org/forum/ubuntu-help/90995-grub-error-17-but-nothings-changed.html)

---

### Post by -gabe-noob- on 2008-01-18
Thanks for a reply I'll put on my reading specs now

---

### Post by -gabe-noob- on 2008-01-18
when I put in -p for e2sfck its not recognizing the command, should I be typing somthing different?

---

### Post by JoshuaRL on 2008-01-18
Hey dude, try to find, download, and burn to a CD SuperGrub.  It should be able to fix any problems you have.  That is, if your HD is being detected.

From what I understand, Grub Error 17 is that the grub file necessary to launch your desired OS can't be found.  There might be several ways this happened:  one time glitch, corrupted file, deleted file, or the HD is broken/not connected.  If it's anything but the last issue, SuperGrub should be able to fix it for you.  Hope that helps man.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by -gabe-noob- on 2008-01-18
How can I download super grup in a Live cd? thats my main problem

---

### Post by JoshuaRL on 2008-01-18
Not sure.  First off, have you checked your BIOS to see if the HD is being recognised?

---

### Post by -gabe-noob- on 2008-01-18
yea I'm not sure how to do that.... :P


but gparted is telling me all my partitions are htere on the live, is that basicly the same thing?
Also I used testdisk on this live and its telling me all my stuff is here 

GPARTED I MEAN G PARTED lol always get htose mixed up

---

### Post by eolson on 2008-01-18
Unfortunately Supergrub doesn't fix error 17.  It fixes just about everything else,  and I highly recommend having a SG CD handy.   It's bailed me out many times cause I'm always messing around with stuff I shouldn't.

---

### Post by -gabe-noob- on 2008-01-18
sooo then how can I fix it:P

---

### Post by JoshuaRL on 2008-01-18
The Live CD mounts its own file system off of the CD.  So G Parted would read everything is there, because it's on the CD.  Did you mount your HD and see if everything is in there?

eolson, wouldn't it fix it if he accidentally deleted the grub file?  Of course, I'm just working from heresay, so I could easily be wrong.

---

### Post by -gabe-noob- on 2008-01-18
how do I mount my HD?

---

### Post by JoshuaRL on 2008-01-18
Try this:

Boot up a live cd

Open a terminal - Applications > Accessories > Terminal

Mount the location of your hard drive version somewhere (replace **** with name of drive, e.g. hda1 or sda2 etc.)

If you're unsure of the drive name type:


```

sudo fdisk -l

```
```

      sudo mkdir /media/hd
      sudo mount /dev/**** /media/hd

```
chroot into your hd drive
```

sudo chroot /media/hd su

```

---

### Post by -gabe-noob- on 2008-01-18
what to do after that 

also the Fdisk thing gave me all my parttions so I used the one on sda1

---

### Post by JoshuaRL on 2008-01-18
Well, try to go to your home folder.  I think your HD is okay since it showed them with fdisk.  Try:

```

cd /home
ls

```

"cd" means change directory.  "ls" means list.  It will tell you what is in the directory you're in.

---

### Post by -gabe-noob- on 2008-01-18
I dont see what your getting at, the reply was gos mekius

---

### Post by JoshuaRL on 2008-01-18
Wha?  You did each line separately, right?

```

cd /home

```

and then:

```

ls

```

---

### Post by -gabe-noob- on 2008-01-18
mhmm it came out in blue, I'm using a gOS live cd right now

---

### Post by bwtranch on 2008-01-19
I haven't seen that many exclamation points since my wife left.

---

### Post by doorknob60 on 2008-01-19
Sorry for going off topic, but gabe, you're not the only 8th grader that uses Ubuntu, but I thought I was :P (Well I guess my friend uses it too...)

---

### Post by JoshuaRL on 2008-01-19
> **bwtranch said:**
> I haven't seen that many exclamation points since my wife left.

God that's awesome.  What, did she leave you through IRL, or were they implied in the conversation?

---

### Post by ubutufan on 2008-01-19
gabe-noob

for anyone here to be able to assist, you need to post the results of
sudo fdisk -l
which was suggested by another person before me
Error 17 indicates that grub is not pointing to the right partition for booting
A brief history how you made the installation/what partitions you used etc would help

---

### Post by -gabe-noob- on 2008-01-19
Hey cool another 8th grader, and I geuss I shoulda known better cause I converted my freind the other week. 

Sorry about not posting the results of that. 

What I think might have done it was my playing around with testdisk and trying to make 1 partition boot over the other. so I did this and next time I tried to go on BAM error 17


also I have an idea. If there is a way to uninstall grub then if I do that will I beable to reinstall it then not have error 17 (cause I know that when its uninstalled you get 22 right?)



For somereason my terminal won't let me coppy so I gotta wright this out



Usage: fdisk [-1] [-b SSZ] [-u] device
E.g.: fdisk /dev/hade (for the first IDE disk
   or: fdisk /dev/sdc (for the third SCSI disk)
   or: fdisk /dev/eda (forthe first PS/2 ESDI drive)
   or: fdisk /dev/rd/c0d0 or: fdisk /dev/ida/c0d0 (for raid devices)
...

To get these results I enterd sudo fdisk


Sorry just realized you wanted fdisk -l here I go again!

SCREW it I'ma go pop in my kbuntu live disk even though its slower!!!

---

### Post by -gabe-noob- on 2008-01-19
here it is streight for the Geubuntu live (had to use this, couldnet find k)

geubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1985    15944481   83  Linux
/dev/sda2   *        1986        9436    59850157+  83  Linux
/dev/sda3            9446        9729     2281230    f  W95 Ext'd (LBA)
/dev/sda5            9446        9541      771088+  82  Linux swap / Solaris
/dev/sda6            9542        9729     1510078+  82  Linux swap / Solaris

---

### Post by Sef on 2008-01-19
This is the GRUB 17 error:

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

1) Since you are dual booting, Windows likes to be one the first partition. 

2) I think you might have overwritten Windows.

3) These three partitions seem to overlap.  

> /dev/sda3 9446 9729 2281230 f W95 Ext'd (LBA)
            /dev/sda5 9446 9541 771088+ 82 Linux swap / Solaris
            /dev/sda6 9542 9729 1510078+ 82 Linux swap / Solaris

Where is sda4?  Is that (sda4) where Windows is located?  If sda3 is the logical partion, that would explain the overlap.

4) Best option would be this:

a) Back up your data, and reinstall everything.  Make sure to put Windows on sda1. 

To help you dual boot from the Live CD, read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

If you want to boot from the alternate cd, read the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/").

---

### Post by -gabe-noob- on 2008-01-19
I'm pretty sure that I deleted my windows partition thru testdisk because I was having problems with my patitions not showing up in gparted. 

I think when I did this I mighta screwed somthing up because I installed gOS right after.

i also tried my 1st manulal partition with this one so I think I put gOS as sda3... hmm did I screw up bad, and how about my reinstall grub idea? or delete gOS and go on with ubuntu alone

---

### Post by Sef on 2008-01-19
> i also tried my 1st manulal partition with this one so I think I put gOS as sda3... hmm did I screw up bad, and how about my reinstall grub idea? or delete gOS and go on with ubuntu alone

I would reinstall everything.  I would wipe out the old partitions then install Ubuntu or gOS or both.   That's how you learn.   I have had to do the same thing before.

---

### Post by -gabe-noob- on 2008-01-20
So my Idea about deleting grub won't work, but I have to wipe EVERYTHING? being the idiot that I am I didnt back anything up.... so if I delete it all my schoolwork will go boom.

---

### Post by -gabe-noob- on 2008-01-20
also I did try to wipe the gOS one but that didn't seem to do anything, and I have ALLL my files on my ubuntu one. I have a external hd and I'm wondering even though its not booting up, can I still save all the stuff to that somehow?

---

### Post by -gabe-noob- on 2008-01-20
BUMP FOR JUSTICE

and anwsers!

---

### Post by Sef on 2008-01-20
> also I did try to wipe the gOS one but that didn't seem to do anything, and I have ALLL my files on my ubuntu one. I have a external hd and I'm wondering even though its not booting up, can I still save all the stuff to that somehow?

Yes, it is possible.   Boot up from the LIve CD.   You should be able to move all your files from your internal hard disk to your external hard disk.  I have moved files off of internal hard disks that didn't boot up using Knoppix.   If you have problems moving them with Ubuntu's Live CD, I would get [Knoppix]("http://knoppix.com").


As for GRUB, you could try and reinstall it.  Worst comes to worse, you still won't be able to boot up.

---

### Post by -gabe-noob- on 2008-01-20
K sef to reinstall grub I just do what I would do to fix error 22 right? or is there another way

---

### Post by -gabe-noob- on 2008-01-20
Damn my lil bro broke the external HD's power cord (FREEKING IDIOT!!!) can I possibly save the files to.. .cd rw's? oh wait lol I'd have to do that from live cd unless. can I instal an os on a small partition then maybe boot that one?

---

### Post by Sef on 2008-01-21
Easiest way is to download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").

---

