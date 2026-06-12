---
title: "Having trouble mounting windows drives"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Jack the R on 2007-03-20
I found and followed the instructions in the user guide for mounting the windows drives.

I now have a /media/windows directory.

Nothing's in it :( 

Did I screw up my fstab?

[img]http://www.extinctionlevelevent.com/misc/linux/fstab_crop.png[/img]

I am using Edgy Eft.

---

### Post by Kateikyoushi on 2007-03-20
Post the output of the following command, it lists your partitions.

> sudo fdisk -l

I assume your windows partition will be sda1 you have to change hda1.

---

### Post by Jack the R on 2007-03-20
Looks like SDA is right, but it could be more complicated than just sda-1.  Here's my info - 

[img]http://www.extinctionlevelevent.com/misc/linux/hard_drive_nfo.png[/img]

What do I need to do?

If it helps, those are all 2 physical hard drives, both 250 gigs.

---

### Post by annda on 2007-03-20
looks like you have 2 nfts partitions: sda2 (partition on the first hard drive) and sdb1(entire disk). choose which one you want to mount (or both?) and change hda1 in your fstab to that.

---

### Post by Jack the R on 2007-03-20
I see no reason not to mount both.

Do the "nls=utf8, umask=0222" parts stay the same for both?

---

### Post by rusty4r on 2007-03-20
Please correct me someone if I'm wrong but isn't it supposed to be "umask=022", and I was wondering about the space in the line between "ntfs" and "nls", I don't think there should be one. Just ntfs,nls=utf8,umask=022. Might not matter just seemed different.

---

### Post by rccharles on 2007-03-20
> **rusty4r said:**
> Please correct me someone if I'm wrong but isn't it supposed to be "umask=022", and I was wondering about the space in the line between "ntfs" and "nls", I don't think there should be one. Just ntfs,nls=utf8,umask=022. Might not matter just seemed different.

The umask bits say what you do not want. 
=== edit ===================================
------ This is incorrect...
A umask=022 say you do not want the ability to run programs in your group and other cannot run programs. A umask=0222 say no one can run programs.  Since it is a windows disk, there probably are not many programs that will run.
------- Comment ...
The "2" bit say you do not want write access. Since the poster is using the read-only ntfs filesystem, I believe umask=0222 is the better option.
=========================================

This comment in  /etc/fstab gives the format of the file:
# <file system> <mount point> <type> <options> <dump> <pass>
which indicates you need a space after ntfs
( a tab probably is acceptable too. )

See:
man fstab
for details.

Robert

---

### Post by Jack the R on 2007-03-21
[img]http://www.extinctionlevelevent.com/misc/linux/snapshot4.png[/img]

Uh oh - it didn't work (I rebooted, and reopened fstab to make sure the changes got saved).

---

### Post by cowlip on 2007-03-21
if you're using ntfs-3g try ntfs-config by givre: [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970) [http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)

---

### Post by Jack the R on 2007-03-21
How do I find out what ntfs it is?

---

### Post by rusty4r on 2007-03-21
> This comment in /etc/fstab gives the format of the file:
# <file system> <mount point> <type> <options> <dump> <pass>
which indicates you need a space after ntfs
( a tab probably is acceptable too. )
Thank you, rccharles, for clearing that up for me.

> The umask bits say what you do not want. A umask=022 say you do not want the ability to run programs in your group and other cannot run programs. A umask=0222 say no one can run programs. Since it is a windows disk, there probably are not many programs that will run.
And I went back to the guide I used and saw that you are correct about this too. [http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

To Jack the R: your fstab still shows you are trying to mount sda2 and sdb1 to the same folder /media/windows

---

### Post by rccharles on 2007-03-21
> **rusty4r said:**
> 
And I went back to the guide I used and saw that you are correct about this too. [http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")



I'd say one out of two.  I got confused about the meaning of the '2' bit. 

The "2" bit says you do not want write access. Since the poster is using the read-only ntfs filesystem, I believe umask=0222 is the better option.  It could be since it is a read-only filesystem that it might not make a difference.

Robert

---

### Post by rccharles on 2007-03-21
> **Jack the R said:**
> 
Uh oh - it didn't work (I rebooted, and reopened fstab to make sure the changes got saved).

Advice, read through this guide to get the idea. This is the best reference I have found on the subject:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)



I see three problems:
1) Is there a period after sda2 and sda1?
    There all over the place. 

2) Notice how you have /media/windows twice?

3) What is the letter f doing here? 
     /def/sda1 should be /dev/sda1

application > accesories > terminal

sudo fdisk -l

# see what names you have.

sudo mkdir /media/your-name-here

sudo nano /fstab

# control -o
# to file

sudo mount -a

To mount what you have done.

Robert

---

### Post by Jack the R on 2007-03-22
> **rccharles said:**
> 
1) Is there a period after sda2 and sda1?
    There all over the place. 

Sorry, is there a simple stupid text editor like Notepad I can use instead of Kate?  I don't understand half the things Kate does.  I'm not entering these periods in, Kate is throwing them in automatically and I'm failing to catch and remove all of them.

Maybe those are periods after sda2 and sdb1.  I thought they were strange but every time I try to delete them, one press of the backspace key takes the number out as well.  So I press the number and no periods and I get a number and apparently also a period.  Just for kicks I entered sdb11 and the first 1 doesn't get the tail/period like the second one does.  Kate is doing something special there, which I'm sure makes perfect sense to a programmer who is familiar with the app, but I am utterly clueless.  Try as I might, I can not get rid of the periods after sda2 and sdb1.  I've gotten rid of the others, but those two are beating me.

I've made the other fixes - if I can get the periods after sda2 adn sdb1 removed maybe this will work.

---

### Post by rccharles on 2007-03-22
> **Jack the R said:**
> Sorry, is there a simple stupid text editor like Notepad I can use instead of Kate?  I don't understand half the things Kate does.  I'm not entering these periods in, Kate is throwing them in automatically and I'm failing to catch and remove all of them.

I suggest nano.  It is very simple.

Applications > Accessories > Terminal

sudo nano /etc/fstab

# it's not fancy
# control-o to save
# control-x to quit

The mouse will not work.  Use the cursor keys.

Other people use gedit

gksudo gedit /etc/fstab

Robert

---

### Post by Jack the R on 2007-03-22
Ooooooh - it works!

Thanks guys!

---

