---
title: "How to &quot;Defragment&quot; in Feisty"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by miqmaq on 2007-06-14
Hi
Is there a utility in Feisty that let you Defragment your hard drive??, and if so how do I access it, if you can help me, could you please use Baby talk, as I am a compete novice/idiot.

Oh! and while I'm here is there another utility that I could use to format a hard disc??.

Thanks for all your many many replies.

Mick:p

---

### Post by Pugwash on 2007-06-14
No need my friend, no need. Welcome to linux.

---

### Post by miqmaq on 2007-06-14
Thanks Pugwash

I'm going to miss doing the housework.

On the other question of formating, I have 2 spare hard discs, that are both in a mess, can I format with Feisty??.

Mick:D

---

### Post by Kobalt on 2007-06-14
Of course. Install Gparted from Synaptic package manager, and partition your disks as you like.

---

### Post by eentonig on 2007-06-14
Linux doesn't suffer from fragmentation as windows.

To format, you can use gparted.And normally, no need to install it. I think it's included by default.

---

### Post by miqmaq on 2007-06-14
Hi Kobalt

I understood the "of course. and install", but the rest sounded like"Clingon", please hold my hand and walk me through it, and please remember the (novice/idiot) part of the original post:D.

Cheers Mick

---

### Post by Kobalt on 2007-06-14
You got it :) 
Go into Applications > Add/Remove. Search for "gparted". Select it and install it.
When it's done, go into System > Admin. > Gnome partition editor. Enter your password, and here you are : you can create/erase partitions, resize them, etc.

---

### Post by bigken on 2007-06-14
to install gparted just go to add remove in the aplications menu type gparted in the search bar and select it to to install then you will find gparted in system/administration ;)

---

### Post by LaRoza on 2007-06-14
You can also get GParted as a Live Cd, it is one of the most useful tools there is.

---

### Post by bigken on 2007-06-14
> **LaRoza said:**
> You can also get GParted as a Live Cd, it is one of the most useful tools there is.


yep I agree :D

---

### Post by buuntuu! on 2007-06-14
and the nice side effect of using the gparted live cd is that you will get the latest version. the repos are always somewhat behind and doing things as sensible as partitioning a hd it's wise to stay on the safe side imo.

---

### Post by jvc26 on 2007-06-14
+1 as an advocate of the GParted LiveCD - a brilliant addition to anyones cd collection.
Il

---

### Post by miqmaq on 2007-06-14
Thanks Kobalt
Thanks Bigken
Thanks LaRoza
Thanks eentonig.

I will certainly take all the advice you've given, but I might not have mentioned that the hard discs I've been on about are not on my system, but are two that I have spare, after another foray, that is to long to go into here but it was a sorry tale:D.

Now let me see if i've got this right, get gparted installed, then remove one of the hard discs on my PC, start gparted and that will let me format the messed up hard disc that I replaced it with?, and then I can do the same with the next hard disc?, please tell me that this is right because I can understand it, of course the first disc i remove would be the slave disc yes?:D.

Cheers Mick

---

### Post by buuntuu! on 2007-06-14
i don't know if the drive will be recognized automaticly, but you could search the forum for "mounting hd" or similar, there are loads of threads about this topic...

---

### Post by LaRoza on 2007-06-14
> **miqmaq said:**
> Thanks Kobalt
Thanks Bigken
Thanks LaRoza
Thanks eentonig.

I will certainly take all the advice you've given, but I might not have mentioned that the hard discs I've been on about are not on my system, but are two that I have spare, after another foray, that is to long to go into here but it was a sorry tale:D.

Now let me see if i've got this right, get gparted installed, then remove one of the hard discs on my PC, start gparted and that will let me format the messed up hard disc that I replaced it with?, and then I can do the same with the next hard disc?, please tell me that this is right because I can understand it, of course the first disc i remove would be the slave disc yes?:D.

Cheers Mick
I never used GParted off a hard disk, only off the Live Cd. When you boot from the cd, it detects, but doesn't mount all disks, including flash drives. It has a nice GUI, and allows you to graphical make changes and then you click "Apply" and you confirm it, and it does its thing. After it is finished, for simple jobs, quite quickly, it will reasess the disks and show you the new layout.

With the Live Cd, any disk connected to the computer will be detected.

---

### Post by miqmaq on 2007-06-14
Thanks LaRoza
I think i'll download the liveCD, it seems a friendlier piece of software than the one on the hard drive which i've just had a look at, I'll have a go at it and let you all know how I got on :D.

Thanks again for all the help.

Mick.

P/S If i'm not back in two days send a search party, and tell Vall I love her :D.

---

### Post by sailor2001 on 2007-06-14
as far as defraging goes.......this is as close to that as you need to be in linux  [http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by Songwind on 2007-06-14
> **LaRoza said:**
> You can also get GParted as a Live Cd, it is one of the most useful tools there is.

The advantage to NOT using it off the live cd is that you cannot accidentally format your main partition. :)

---

### Post by LaRoza on 2007-06-14
> **Songwind said:**
> The advantage to NOT using it off the live cd is that you cannot accidentally format your main partition. :)

True, but you can un-hook it. I do that sometimes when I want to be sure a disk is untouched. I do not doubt the usefulness of GParted, live or not, but I have only used the live disk and am most familiar with that.

---

### Post by nymphaeles on 2007-06-14
I don't really want to give you the wrong impression that ext3 file system doesn't get fragmented.  In fact, both ext2 and ext3 file systems do get fragmented over time.  There is no online defragment utility, but there is an offline defragmentation utility for ext2 (doesn't work with ext3) called e2defrag.  The ext3 file system; however, uses a very efficient system of inodes and blocks along with a journaling system that eliminate many file system checks and thus seems to overcome the fragmentation problem effectively.  The simplest way to attain a defragment on user's space is doing a backup/restore procedure.

---

### Post by Quintin Riis on 2007-06-25
This question comes up a lot it seems.  

Someone said Linux doesn't suffer from fragmentation.. this isn't entirely true.  But fragmentation rarely seriously impacts performance.  

If you use the XFS file system you can defragment it while it's online.

Article we wrote: 

[http://daecom.biz/ask/2007/06/25/how-do-i-defragment-my-hard-drive-in-linux/#more-8](http://daecom.biz/ask/2007/06/25/how-do-i-defragment-my-hard-drive-in-linux/#more-8)

---

