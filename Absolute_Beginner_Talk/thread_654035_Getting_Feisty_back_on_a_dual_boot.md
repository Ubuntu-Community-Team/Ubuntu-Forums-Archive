---
title: "Getting Feisty back on a dual boot"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by penguinbreath on 2007-12-30
After I had some problems after my upgrade to Kubuntu Gutsy on my secondary system, I decided to do a fresh install of Ubuntu Gutsy with a Windows XP dual boot. 
    Gutsy is still giving me some problems. I got everything working, but things are just being sluggish and a bit buggy. ( Might be my hardware)
   Feisty ran very well on this machine, so I want to install it again.

What is a simple way to replace Gutsy with Feisty without formating my drive? ( And then installing Windows again) 

Would it be better if I make a triple boot  on my system? ( *ubuntu 7.04 + Ubuntu 7.10 + Win XP)  And can I make a triple boot with a *ubuntu live CD?

---

### Post by forestpixie on 2007-12-30
you can just install with feisty on top of the gutsy install using the same partition

---

### Post by penguinbreath on 2007-12-30
Sorry for this silly question, but where can I download the 7.04 version of (K)ubuntu? I am looking on the Kubuntu web site but I can't seem to find it.

---

### Post by forestpixie on 2007-12-30
which country you in
Edit  - if you go here [http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php)

pick somewhere close to you - then you'll get page similar to this - [http://www.mirrorservice.org/sites/releases.ubuntu.com/kubuntu/gutsy/](http://www.mirrorservice.org/sites/releases.ubuntu.com/kubuntu/gutsy/) (this is the uk page)

near the top where it has 'platform' go to kubuntu and you'll go back to the different versions - pick 7.04 and you're off

---

### Post by penguinbreath on 2007-12-30
> which country you in

I am in the US.

---

### Post by forestpixie on 2007-12-30
you can get 7.04 from mit

[http://ubuntu.media.mit.edu/ubuntu-releases/kubuntu/](http://ubuntu.media.mit.edu/ubuntu-releases/kubuntu/)

wouldn't know if it's near you or not - with some of the sites ypou can navigate backwards - parent directory or similar

---

### Post by penguinbreath on 2007-12-30
Alright the download is working well, thank you!
 
I still wonder if I should try a triple boot with Feisty?

---

### Post by forestpixie on 2007-12-30
I guess it wouldn't be a problem - it'd just mean a bit of partition work - not a good idea to share /home apparently - but you wouldn't need another swap

---

### Post by penguinbreath on 2007-12-30
> I guess it wouldn't be a problem - it'd just mean a bit of partition work - not a good idea to share /home apparently - but you wouldn't need another swap

I don't think I have a separate home partition on this computer. So couldn't I just do a normal *ubuntu 7.04 install like I did when I made with my current dual boot setup?

This computer is only used for browsing the web and printing, so I would not need it to share data across partitions.

---

### Post by forestpixie on 2007-12-30
yea - sounds good to me if you've not got separate /home now - you'd need a new partition to install feisty onto and you should be cooking with gas :)

I would be inclined to make sure you've got the partitioning sorted before you started the install, mostly because I just prefer to do it that way - I use a gparted livecd to do mine - then use the manual partition option when you get there

---

### Post by penguinbreath on 2007-12-30
> yea - sounds good to me if you've not got separate /home now - you'd need a new partition to install feisty onto and you should be cooking with gas

I would be inclined to make sure you've got the partitioning sorted before you started the install, mostly because I just prefer to do it that way - I use a gparted livecd to do mine - then use the manual partition option when you get there

So you do not recommend me doing the auto-partition/install thing from the live CD?

---

### Post by penguinbreath on 2007-12-30
[[IMG]http://img295.imageshack.us/img295/9522/screenshotdevhdagpartedkn3.th.png[/IMG]](http://img295.imageshack.us/my.php?image=screenshotdevhdagpartedkn3.png)

This is what the hard drive looks like on my secondary system.


I noticed the Windows partition is really big. I probably would want to shrink it about as small as I can since I really don't use Windows to much. I am just keeping it in case I need to install a Windows-only application. So I would probably like a few spare GBs on it. 

What should I do now? I have partitioned a hard drive before, but never with other operating systems on it.

I want to try a triple boot.

---

### Post by forestpixie on 2007-12-31
you can use the gparted on the gutsy livecd - or get gparted from [here]("http://gparted-livecd.tuxfamily.org/") - burn it as an iso and boot with it.

Then resize which ever partition you want to allow enough room for the feisty install, format it to ext3, then boot with the feisty disc and using the manual option install to your new partition

But be aware that you can only have 4 primary partitions on one hdd

I guess there was some sort of scrnshot on your last post - it's not there :)

Edit - before you do any work, either yourself, or with an installer - make sure you have an effective backup of any data you can't lose

---

### Post by penguinbreath on 2007-12-31
[[IMG]http://img299.imageshack.us/img299/5365/screenshotdevhdagpartedcj2.th.png[/IMG]](http://img299.imageshack.us/my.php?image=screenshotdevhdagpartedcj2.png)

Here is the image of my hard drive.

I will do a defragment on my windows partition and I will resize it. I got Gparted out of add/remove programs. I got no important data on this PC so I am not to worried about blowing the thing.

Is there any other preparation I need to do?

---

### Post by forestpixie on 2007-12-31
the gparted in add/remove isn't a livecd - there's a version on the gutsy livecd I think otherwise go [here]("http://gparted.sourceforge.net/") and burn as an iso - then you can boot with it

anyway looks easy enough - resize the ntfs to make it smaller - make a new partition in the unallocated space, format to ext3 and install feisty to it

maybe get [supergrub]("http://supergrub.forjamari.linex.org/") as well - it's as well to be prepared and it's worth having about just in case you get a problem booting, it's another livecd - so burn it as iso if you bother

you can use the livecd to install grub - but I always found it quicker to boot the supergrub

hope that's some help

almost forgot - give win a couple of defrags

---

### Post by penguinbreath on 2008-01-01
[[IMG]http://img98.imageshack.us/img98/268/screenshotdevhdagparteduw9.th.png[/IMG]](http://img98.imageshack.us/my.php?image=screenshotdevhdagparteduw9.png)

I got the hard drive resized and partitioned with the Gparted live CD. For some reason there is about 500mb used on the new partition, which is strange? Anyways it appears everything is working ok.


Now I need to install Kubuntu 7.04. I load the live cd, and I click install and get to the partitioning part, I click manual, and from there I have no clue on what to do. :(

---

