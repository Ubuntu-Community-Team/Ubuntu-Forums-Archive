---
title: "plz troubleshoot this!"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-09-26
my pc was dual boot with xp and dapper one week ago.then i tried to test edubuntu.so i installed it on another drive.it installed and worked properly. when i tried to boot ubuntu it generated an error.in that time i didn't had net connection ,so i could not ask this problem online.i needed ubuntu badly because i wanted some plots and calculations on octave for one of my projects. so i picked up dapper cd and removed the edubuntu and installed ubuntu on that drive.this solved my problem and i was able to recover my old ubuntu .now i have two ubuntus installed on two different drives.i use only my old ubuntu because my useful softwares on it and nothing on my new ubuntu.now i want to remove xp and ubuntu installed a week ago(new ubuntu) without affecting my old ubuntu. i want to do this from my old ubuntu.i want to change the format of ntfs to the one which ubuntu can use properly.plz tell me what format i should specify for ntfs partition after formatting it.
in short i want to format two drives from ubuntu installed on third drive.how can i do this?
note that grub is now on my master boot record.this was placed by my new ubuntu.so would formatting of that ubuntu remove grub from master boot record? if so then how to prevent this?
thanks in advance.

---

### Post by xyz on 2006-09-26
You sure seem to have sufficient knowledge in the field to come up with a title that reflect what you need to solve.
Please don't take it wrong; I've read lots lately about moderators (don't they do enough for us?) having a problem with thread titles.
They shouldn't have to do the exta job of retitling a thread esp. since you do seem to know what you're talking about.

A good title also (and simply) help other members/visitors with the same question to relate to your thread. Which is one of a thread's goal.
Thank you for your understanding.

---

### Post by u04f061 on 2006-09-26
thanks for your nice reply.the reason why i mistitled my post is that ,i thought for more than 5 or 6 minutes about the title of my post.since it seemed an ambiguous topic to me. so i could not title it correctly accorting to its main idea. hence instead of giving it some title , i made a request to my forum friends to have a look at it and try to help me.
thanks once again.
i think i would be careful about the titles as well next time because of your nice suggestion.

---

### Post by xyz on 2006-09-26
Cool ;) 
Just an idea for a title:
> Formating 2 drives from ubuntu installed on 3rd drive?

Hey u04f061 I've done this myself and may just do it again from time to time. And I know it can take FOREVER to come up with a title when we don't know where to start.
Thanks to you, though - will get back when I can.

---

### Post by xyz on 2006-09-26
Just to ry and see the tree among the forest...let's try and run this command.
Please post the output.
```
sudo fdisk -l

```

---

### Post by Klaidas on 2006-09-26
A helpful offtopic suggestion:

Press the spacebar after a sign (. , ; : "" whatever)
It will be easier to read :)

---

### Post by u04f061 on 2006-09-26
> **xyz said:**
> Just to ry and see the tree among the forest...let's try and run this command.
Please post the output.
```
sudo fdisk -l

```

ejaz@msiddique:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1028     8257378+   7  HPFS/NTFS
/dev/hda2            1029        2430    11261565    f  W95 Ext'd (LBA)
/dev/hda5            1666        1698      265041   82  Linux swap / Solaris
/dev/hda6            1699        2430     5879758+  83  Linux
/dev/hda7            1029        1665     5116639+  83  Linux

Partition table entries are not in disk order
ejaz@msiddique:~$

---

### Post by xyz on 2006-09-26
About this...

> Mounting Linux Partitions/Drives in Ubuntu
If you plug in an external hard drive with a Linux filesystem, it will automount and show up on your desktop, just like any external media.

But what if you have an internal hard drive or partition with a Linux filesystem? Well, that's what this tutorial is about. 

[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by wieman01 on 2006-09-26
> **xyz said:**
> You sure seem to have sufficient knowledge in the field to come up with a title that reflect what you need to solve...[..]..since you do seem to know what you're talking about.
Although you have a point, this is not a nice thing to say. We all started off somewhere and I well remember the time when I "did not know what I was talking about".

And yet, a nice title would help next time you post, U04f061. Now let's get down to the nitty-gritty...

---

### Post by wieman01 on 2006-09-26
> **xyz said:**
> Just to ry and see the tree among the forest...
It's the wood for the trees, mate. :-)

---

### Post by xyz on 2006-09-26
> **wieman01 said:**
> Although you have a point, this is not a nice thing to say. We all started off somewhere and I well remember the time when I "did not know what I was talking about".

And yet, a nice title would help next time you post, U04f061. Now let's get down to the nitty-gritty...

It's a compliment, mate and he seems to have understood what I meant! 
The way he describes the problem showed he knew what he was talking about and therefore could come up with a decent title.

We're not in an English course...and it was a play on words based on the expression the wood for the trees!!the tree being the linux tree!
Are we really here to waste time on this?

---

### Post by u04f061 on 2006-09-26
> **xyz said:**
> It's a compliment, mate and he seems to have understood what I meant! 
The way he describes the problem showed he knew what he was talking about and therefore could come up with a decent title.

We're not in an English course...and it was a play on words based on the expression the wood for the trees!!the tree being the linux tree!
Are we really here to waste time on this?

plz stop posting if you can't solve my trouble. it is not the place of war.i posted here to get solution to my problem. can you solve it?

---

### Post by xyz on 2006-09-26
> **u04f061 said:**
> plz stop posting if you can't solve my trouble. it is not the place of war.i posted here to get solution to my problem. can you solve it?

Sure...let's all cool down but please remember we're not at your disposal..like fingersnapping! It's all on free time!

I posted twice to try to help; you didn't respond! Did it work? Did you check out the link? If so, ....I mean!

---

### Post by u04f061 on 2006-09-26
yes i went to this link.it is not for formatting drive. it is for mounting a drive.my drives are already mounted.and i want to format them.if you ever used windows,when we select a partition and right click on it ,it offers option format.i want to do that.

moreover i don't know is it problem with firefox or site that the images it displays or just white pages on my firefox. so i can't see images

---

### Post by wieman01 on 2006-09-26
Formating is best done with the Ubuntu Live CD. You boot it, fire up "Gnome Partition Editor" and format your partitions. Should it occur that GRUB gets lost in the attempt (which I doubt) try this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

If you still have problems, we are here to help.

---

