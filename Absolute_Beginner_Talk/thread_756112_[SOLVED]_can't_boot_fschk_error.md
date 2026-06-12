---
title: "[SOLVED] can't boot fschk error"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by gitpik on 2008-04-15
Alright. So I've been using ubuntu since the last month of fiesty and I'm really quite happy with it. So much so that when I finally ran out of disk space I decided to remove windows completely. What I did was transfer all my important stuff to my new hard drive (I now have 2 320 gig sata drives: sda and sdb) reformat the original drive and reinstall ubuntu. I had everything all set up and just after I finished moving everything back onto my first drive and organizing I thought I would then reformat my new drive since it was now empty. I also thought it would be really smart to do this with gparted from within ubuntu and not with the live cd (as I see now I should have done). What I did basically last time I was able to boot was unmount the 2 partitions on the second drive with gparted (one ntfs and one ext3) set a new disk label of the msdos type (wasn't really sure if this was the right choice but it was the default) and then formatted the whole drive as one ext3 partition. Everything went smoothly and I figured I couldn't do any harm to my ubuntu install since it was on a completely different physical drive (beginners foolishness) 

Now when I rebooted I got the splash screen up to about 1/4 of the bar full then a blank screen with a cursor. So I went for recovery mode from what I can tell fschk stopped with error code 8 on the partition I have for /home (sda3) then spits me out at the root prompt. I was able to boot to the gparted live cd and according to that program the partitions have the right amount of data there and are all intact. (which would be really cool cause it all important stuff of course and I know I should have backed up before hand). 

So I have 2 questions then 

1) (the obvious) is there anyway to fix this or have I hosed all my data?

2)Since it appears that all my data is intact and it's all on it's own /home partition would it be easiest to just reinstall the system and not format my /home partition hopefully leaving everything there. this is what I usually do and it's worked every time so far but I would rather learn about what I broke and how I can fix it.

When I get home tonight (about 7 PST) I will post the actual error log file but maybe someone could point me in the right direction and I could have a couple things to try. Thank you very much in advance, this community has been a humongous help to me already.:guitar:

---

### Post by forestpixie on 2008-04-15
I have had this when playing with partitions - the UUID changes so that fstab can't find the partition. You can use nano at the prompt to edit the fstab file.

You could either get the new UUId with ```
blkid
``` and edit fstab with nano 

nano /etc/fstab 
Ctrl+O then enter saves the file, Ctrl+X closes nano

or change the entry to be without the UUID, which is a bit easier - eg

> # /dev/sda3
UUID=0a4ebd39-4085-4c93-a45d-1fbd60527046 none swap sw 0 0

> # /dev/sda3
/dev/sda3 none swap sw 0 0

---

### Post by gitpik on 2008-04-15
Thank you forestpixie! I will try that as soon as I get home and let you know how it works out! :D

Edit: Every thing's back and now I know how to fstab!

---

