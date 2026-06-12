---
title: "What should be the SWAP size??"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by rohit88 on 2007-08-27
M a noob ....I am going to dual boot ubuntu with xp..
I've read something about swap file in some book..
so what size should i got for swap partition
(I am using 30-40GB HD for linux)


Its cofig- amd64 5000+
asus mb
2gb ram and 250 hd

---

### Post by forestpixie on 2007-08-27
supposedly 2 times RAM - but with 2Gb I don't think that's needed - I've 1Gb and 998 Mb swap which rarely gets touched - I saw someone the other day suggesting 512Mb with 2Gb RAM

---

### Post by Imsati on 2007-08-27
Do a search for Swap Size and you'll get a plethora of debates.

I'm a die-hard fan of Swap = 2x physical RAM, myself. I only have 1 gig of RAM though compared to your 2. When all debates are over though, you obviously have the HDD space, so why not just make Swap 4 gigs. You can always adjust it later.

--Jay

---

### Post by Outrunner on 2007-08-27
> **Imsati said:**
> Do a search for Swap Size and you'll get a plethora of debates.

I'm a die-hard fan of Swap = 2x physical RAM, myself. I only have 1 gig of RAM though compared to your 2. When all debates are over though, you obviously have the HDD space, so why not just make Swap 4 gigs. You can always adjust it later.

--Jay

4GBs? That's insane! A normal user would never use that much... With 2GBs of RAM, 512MBs of swap should be enough. I have 1GB of RAM and 1 GB of swap, and I've never seen my swap partition get touched before.

---

### Post by forestpixie on 2007-08-27
> Do a search for Swap Size and you'll get a plethora of debates.

Indeed :D

But I do think that unless the OP is going to be using a lot of really memory intensive work - 512Mb would be enough with 2Gb RAM.

I think the most of my swap I've seen used was about 30Mb with 1 Gb RAM

---

### Post by Haegin on 2007-08-27
The old rule used to be that your swap should be twice the size of your RAM. With newer machines which have more RAM this is less of an issue. I have 2GB of RAM and have two 1GB swap partitions (if you split the swap between drives it can be faster in some circumstances) so I recommend a single 2GB swap partition for your computer.

I generally say if you have less than 1GB of RAM then make your swap partition twice the size of the RAM, if you have more than 1GB of RAM then make the swap partition the same size as your RAM.

---

### Post by rohit88 on 2007-08-27
M confused:confused:

can someone tell me why do we need swap ...so that i can think:lolflag: on it

---

### Post by insane_alien on 2007-08-27
if you want to hibernate the computer, 2.1GB if you don't, 512MB or less if you want.

---

### Post by forestpixie on 2007-08-27
> **insane_alien said:**
> if you want to hibernate the computer, 2.1GB if you don't, 512MB or less if you want.
 +1

> Linux uses swap space as "extra" memory for pages of application
memory that are not being actively

Swap is similar to the way the page file in win works - but Linux uses up all your RAM first - it's quicker to read.

Sorry if you're confused - I'd say have some but it depends what you're going to be doing as to how much.   For general use go for the 512Mb - but if you want to hibernate you'll need more.

---

### Post by chrome307 on 2007-08-27
It's very bewildering the comments made so far ....... when I look at my default installation this is what I have  - ( 512MB RAM ) .... generally I see 33MB being used in the SWAP partition .............. could I reduce the size of the this to 1GB (or leave it as it is?) .... I don't use hibernation.

[IMG]http://i16.tinypic.com/4lrajj6.jpg[/IMG]

---

### Post by Outrunner on 2007-08-27
> **chrome307 said:**
> It's very bewildering the comments made so far ....... when I look at my default installation this is what I have  - ( 512MB RAM ) .... generally I see 33MB being used in the SWAP partition .............. could I reduce the size of the this to 1GB (or leave it as it is?) .... I don't use hibernation.

Yes, you can. You'll have to boot into the LiveCD, though, because you can't resize a partition while it's mounted. And then don't forget to add the unallocated space to one of your other partitions

---

### Post by chrome307 on 2007-08-27
Which partition would benefit from this most (extended or primary) ?

And how do I go back changing this via the LiveCD ??

Some simple steps would be helpful if possible?

---

### Post by wahoobob on 2007-08-27
I am having trouble with my hibernation.  Any ideas about how to get it working?  I have a IBM R51 thinkpad running 7.04 and two swap files have been created... used to dual boot XP but now its all Ubuntu.  Since the XP delete I can't hibernate the machine.  I am not the most techy of users so what would be the easiest fix?

---

### Post by Outrunner on 2007-08-27
[QUOTE="chrome307"]Which partition would benefit from this most (extended or primary) ?

And how do I go back changing this via the LiveCD ??

Some simple steps would be helpful if possible? [/QUOTE]

The process is quite simple actually :)

After you access the LiveCD, you should be able to find 'Gnome Partition Editor' in the menus(System-> Administration, I think, not on Gnome right now). Then right click on your swap partition and and click "Resize/Move". After you're done, click 'Apply' 

NOTE: To allocate the unallocated space to your primary partition,  you will have to drag the cylinder from LEFT to RIGHT (see screenshot).

Then right click on your primary partition and select "Resize/Move" and give the unallocated space to it. After you click apply, you're done!

EDIT: And to answer your first question, it would be best the give the space to the primary partition. It wouldn't make much sense to give it to the Extended partition, since that's where your swap partition resides, right ;)

---

### Post by jayaramk on 2007-08-27
it must be around double the ram of ur pc!!!

---

### Post by Outrunner on 2007-08-27
> **jayaramk said:**
> it must be around double the ram of ur pc!!!

Not sure if you were joking or not, but this statement comes from the era where dinosaurs ruled the earth. Or at least, when computers had a maximum of 64 MBs of RAM or something like that... Really, it doesn't apply nowadays.

---

### Post by raijinsetsu on 2007-08-27
Just a general kernel of knowledge: the stock 32-bit kernels cannot access more than 3gb of memory. This means, if you have 2gb of RAM anything more than 1gb of swap is wasted. 64-bit kernels do not have this limitation, in which case I'd make RAM and SWAP 1 for 1.
However, unless you're running multiple database servers or have thousands of concurrent users you will not get any benefit from having more than 3 or 4gb of total memory.

---

### Post by akba0012 on 2007-08-27
I run a lot of applications across many workspaces and never had to use the swap. I have 1.5 gigs of ram, i would say keep the swap file size as low as possible. 512meg seems really comfortable and dooable.

---

### Post by fallencyi on 2007-08-27
> **akba0012 said:**
> I run a lot of applications across many workspaces and never had to use the swap. I have 1.5 gigs of ram, i would say keep the swap file size as low as possible. 512meg seems really comfortable and dooable.

I have a question that seems to fit in this discussion: 

will using 4gb of swap space hurt anything other than the fact that I am "Wasting 2.5gb of HDD space?"

 (I had 2gb ram & followed the "Outdated" advise of 2x Ram because at the time I didnt know to question that advise)

---

### Post by raijinsetsu on 2007-08-27
> **fallencyi said:**
> I have a question that seems to fit in this discussion: 

will using 4gb of swap space hurt anything other than the fact that I am "Wasting 2.5gb of HDD space?"

 (I had 2gb ram & followed the "Outdated" advise of 2x Ram because at the time I didnt know to question that advise)
Refer to my post above... 4gb of swap will not get used on a 32-bit system, and would be useless on most 64-bit systems with 2gb of ram.
It will not HURT anything though.

---

### Post by Haegin on 2007-08-27
To be honest, if you have a massive (320GB+) hard drive you probably won't fill it up unless you are doing video editing or a similar activity that uses large files. If you are then you will probably need the swap to make handling the large files easier. If you don't then you most likely won't fill the drive so you will probably never need the space you may have "wasted" on swap.

Of course if you have a smaller drive or just a massive prawn collection then you should ignore this post.

There is some good advice about swap on the Linux documentation project here: [http://tldp.org/HOWTO/Partition/requirements.html#SwapSize](http://tldp.org/HOWTO/Partition/requirements.html#SwapSize)
That includes good advice about where to put the swap on your drives.
[quote="The Linux Documentation Project"]
Put your swap on a fast disk with many heads that is not busy doing other things. If you have multiple disks: Split swap and scatter it over all your disks or even different controllers.
[/quote]

---

### Post by anewguy on 2007-08-27
Okay, I've looked at that guide, and now have a question.  In the "old days" we could place a separate backing store just for the system software, and up to "x" backing stores for regular process usage.  So, can you create and dedicate a swap just for Linux, and a separate swap for other processes?  Of course, in those days we also spread the load across multiple disks - system and system backing store on 1 disk, 1 regular backing store also on that disk.  Any additional backing stores were spread amongst drives depending upon the number of i/o's per second going thru the controller and the device.  I know that on a single user home system this would all be moot, but when you move into servers with multiple users, do the "old ways" still apply?:)

---

### Post by Gruelius on 2007-08-27
I would say 120% of your ram size so hibernation is possible. Ive never really stressed my machine under linux but usually the swap doesnt get touched.

---

