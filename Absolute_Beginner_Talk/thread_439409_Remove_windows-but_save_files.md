---
title: "Remove windows-but save files"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by tomt on 2007-05-10
Hi,

I installed Ubuntu because windows had finally given up and died on my system. Although I have a few configuration problems-(I cant get wireless yet, and i use a vaio but can't get full wide screen grr) I'm impressed enough that I want to just use Ubuntu (windows wont work anyway ;) )

The problem is I dont really understand how to install Ubuntu without having a windows partition without losing all my old documents and media files. Can anyone help?

Cheers,

tomt

---

### Post by ikonia on 2007-05-10
this ones an easy one,

mount your windows disk read only using the mount command,

copy all the files you want from your windows partition to you ubuntu disk

unmount the windows partion using the umount command

Destroy the windows partition

Use gparted to resize your ubuntu disk to take up the rest of the space, or create a new file system on the old partition and mount in under ubuntu

Bingo - your all done

---

### Post by ikonia on 2007-05-10
oooh and don't forget to remove the window entry from your /boot/grub/menu.lst file - doesn't really matter but its nice to be tidy as windows no longer exists on your computer.

---

### Post by tomt on 2007-05-10
What if there is not enough space on the Ubuntu side of the partition for the files on the windows side.

Also could you provide instructions suitable for a moron. ;)

---

### Post by bodhi.zazen on 2007-05-10
If there is not enough room you will have to make room or save to an external media (flash drive, CD, DVD).

To mount : 

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

---

### Post by tomt on 2007-05-10
Cheers, think I'm beginning to see how I go about this. 

2 questions:

1) I have 50 gigs I need to move, is there really no better way than maxing out all my USB's and blank DVDs ?

2) Windows is not working at all. I can see the files as read only via Ubuntu-will I be able to send these to USB.

ty

---

### Post by annda on 2007-05-10
> **tomt said:**
> Cheers, think I'm beginning to see how I go about this. 

2 questions:

1) I have 50 gigs I need to move, is there really no better way than maxing out all my USB's and blank DVDs ?

2) Windows is not working at all. I can see the files as read only via Ubuntu-will I be able to send these to USB.

ty

1. i understand you have ubuntu already installed. you can move some videos etc. to ubuntu partition temporarily and compress any other files. burn the rest.

2. if you can read it, you can copy it. just not change.

---

### Post by bodhi.zazen on 2007-05-10
Wow, 50 Gb is huge.

Well, you need to put it somewhere, so you need 50 Gb of storage, unless you can compress it in an archive (like a zip file).

How to archive : [http://www.linuxjournal.com/article/9370](http://www.linuxjournal.com/article/9370)

So yes, painful as it may seem, you need 50 Gb of storage space :twisted:

You should be able to move files to a usb device no problem.

---

### Post by tomt on 2007-05-11
Right so there really is no way for me to weasle round copying my files. Thanks for the help so far the last bit of explanation I need relates to Ikonia's first helpful post:

> **ikonia said:**
> this ones an easy one,

mount your windows disk read only using the mount command,

copy all the files you want from your windows partition to you ubuntu disk

unmount the windows partion using the umount command

Destroy the windows partition

Use gparted to resize your ubuntu disk to take up the rest of the space, or create a new file system on the old partition and mount in under ubuntu

Bingo - your all done

1-how do I mount my windows disk-what is the mount command

2-how do I unmount

3-how do I destroy the windows partition

4-what is gparted and how do I use it to resize my ubunut disk?


I appreciate anyone reading this is probably struck dumb by my ignorance but if you do manager to pick yourself off the floor any guidance would be incredibly valuable.

Finally! I have heard that occasionally thumbsticks and cd/dvd burners dont work on initial Ubunut install. Anyone know how I can make sure mine does, or get it working. 
I'm stuck at work right now but hope to carry out this exercise when I get home tonight. I'll let you all know how I do.

THANKS

---

### Post by bodhi.zazen on 2007-05-11
> **tomt said:**
> Right so there really is no way for me to weasle round copying my files. Thanks for the help so far the last bit of explanation I need relates to Ikonia's first helpful post:



1-how do I mount my windows disk-what is the mount command

2-how do I unmount

Look ....  Up ....

Post #5 covers these questions ...

> 3-how do I destroy the windows partition

4-what is gparted and how do I use it to resize my ubunut disk?

You can "destroy" the windows partition in several ways. Easiest is to re-format it. This can be done in several ways, including with gparted. What you do with the free space is up to you. You can add it to Ubuntu, or mount it as a data partition, etc ....

GParted:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-6.iso)


> I appreciate anyone reading this is probably struck dumb by my ignorance but if you do manager to pick yourself off the floor any guidance would be incredibly valuable.

LOL. 

I think you will find Ubuntu welcomes new users.

> Finally! I have heard that occasionally thumbsticks and cd/dvd burners dont work on initial Ubunut install. Anyone know how I can make sure mine does, or get it working. 
I'm stuck at work right now but hope to carry out this exercise when I get home tonight. I'll let you all know how I do.

THANKS

Yea, there can be hardware problems. Best way to test is with the live (desktop) cd. If your hardware (usb drive, CD/DVD) drive works you should be fine after a hard drive install.

IMO fiesty is the best version, although that does not mean "problem free" or that some users for some hardware have better luck with Edgy or Dapper. IMO most do best with Feisty.

Welcome to Ubutnu !

---

### Post by tomt on 2007-05-12
Thanks all. I did finally manage to remove windows, what i ended up doing was getting the files onto a a few usb's and cds then just reinstalling ubuntu but over the whole disk...

#thanks again!

tomt

---

