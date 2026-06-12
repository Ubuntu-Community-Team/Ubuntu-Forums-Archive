---
title: "Partitions - XP and Ubuntu."
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Moonshine on 2006-05-30
Hey all,

I've used Ubuntu before, but on an old PC and I really enjoyed my experiences with it. Now I'd like to bring ubuntu to my computer, and see if I can convert myself from XP to Ubuntu for the majority of the time.

However, before I can install ubuntu I would like to know what would be best as afar as partitions are concerned.

I have;

C: Drive - 120GB - Currently has Windows XP installed, but about 90GB free. Is it possible to create another partition on this drive, even though it has data already on it? Are there any free applications that would allow me to do this? This drive also has a 5GB unformatted partition, that use to have recovery software, but that has been deleted so it is just wasted space.

D: Drive - 160GB - Data storage, about 30GB free. I can access the documents on this drive regardless of what operating system I am using, right?

Ideally, I would like to be able to create another partition in the C: Drive, as most of the space isnt being used anyway, but I don't want to have to reinstall Windows XP. Is this possible?

I am also a little confused about the difference between primary, extended and logical drives, and which would be needed in this situation.

Thankyou for your help :D

edit: Ah yes, and I've heard something about a swap drive...double the system memory or similar?

---

### Post by macdo on 2006-05-30
You've got thirty Gig, give or take on your hda (that's like C:\, in Linux.)
First step is to back all that up onto your other hard drive.

Then boot up with the livecd and use Gparted to resize the partition on hda, so that the partitioning table looks something like this (sizes are just an example, of course): 
hda1: 30G, formated as NTFS, Windows
hda2: 2G, formated as linux-swap, Swap
hda3: 8G, formated as ext3, / (the main linux file system)
hda4: 80G, formated as ext3, /home (Your personal part of Linux. It's best to have this on a separate partition, because that way if you ever need to reinstall, you can not format this one, and not lose all your stuff (data, preferences, bookmarks, contacts in Gaim, whatever))

Your hdb (currently your D:\ drive), needs to be formated as win32 if you want to be able to access it with both linux and windows. Linux can't write to NTFS, and Windows can't even read ext3 :-(

Don't hesitate to ask if you need any further explanations!

---

### Post by meborc on 2006-05-30
what i would do is:

1. backup the stuff i can't live without
2. defrag defrag defrag win as long as i can see free space AT THE END of the partition (in defrag)
3. slip in ubuntu install cd and boot from it
4. at the partitioning stage RESIZE the win partition smaller (in your case to size of 50G - just in case)
5. then chose the FREE SPACE and option AUTOMATICAL PARTITIONING (the partitioner will create the filesystem and the swap partition in the free space

this is in case you don'd need extra partition for your /home... otherwize create the /home partition BEFORE chosing the automatic partitioning...

hope that helps... ;)

EDIT: and windows CAN read linux file systems... not by default, but with a help of a little patch... search google for more info on that :D

---

### Post by aysiu on 2006-05-30
meborc is right on.

If you need a walkthrough on setting up a dual-boot for Breezy, check out this:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

If you can wait two days until Dapper (or install the release candidate now), check out this:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

If you want access to Ubuntu files from Windows, check out this:
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by Moonshine on 2006-05-30
Thanks for your replies, very helpful.

If I install the Release Candidate of Dapper, can that be updated to the proper version after its installed or would the actual release need to be reinstalled?

Thanks again.


Quote:
Originally Posted by Moonshine
Thanks for your replies, very helpful.

If I install the Release Candidate of Dapper, can that be updated to the proper version after its installed or would the actual release need to be reinstalled?

Thanks again.

edit: Also, if I select the "Resize IDE1 master, partition #1 (hda) and use freed space" will this resize my current C:\ Drive, and install ubuntu as well without affecting the Windows Installation, because if thats what it does then it sounds like a good option? However, I'd still like to have plenty of space for the Windows Installation. Does it simply take what it requires, or shrinks the windows partition down as small as it can go? I'd like Windows to have at least 30GB, and Ubuntu can have another 30, or something like that? Sorry if I'm kinda confusing. Will it take care of the swap drive?

Thanks again for your very helpful responses :D

---

### Post by Moonshine on 2006-05-30
Whoops, double post, sorry!

---

### Post by aysiu on 2006-05-30
[QUOTE=Moonshine]Thanks for your replies, very helpful.

If I install the Release Candidate of Dapper, can that be updated to the proper version after its installed or would the actual release need to be reinstalled?

Thanks again.[/QUOTE] It can be updated quite easily. In fact, unless you turn the update notifier off, you'll be notified of updates as they happen.

As long as you keep up with the updates, it's just about the same as installing the final version.

---

### Post by Moonshine on 2006-05-31
[QUOTE=aysiu]
As long as you keep up with the updates, it's just about the same as installing the final version.[/QUOTE]

Excellent, thanks.

So just one question remains...

If I select the "Resize IDE1 master, partition #1 (hda) and use freed space" option when installing ubuntu, what exactly will it do? Will it create another partition on my C: drive for ubuntu, and keep the rest for XP, or take as much as it can for ubuntu and leave xp with as little as necessary? I would like them both to have about 30GB if possible.

Thanks again! :)

---

### Post by aysiu on 2006-05-31
[QUOTE=Moonshine]Excellent, thanks.

So just one question remains...

If I select the "Resize IDE1 master, partition #1 (hda) and use freed space" option when installing ubuntu, what exactly will it do? Will it create another partition on my C: drive for ubuntu, and keep the rest for XP, or take as much as it can for ubuntu and leave xp with as little as necessary? I would like them both to have about 30GB if possible.

Thanks again! :)[/QUOTE] To be honest, I don't know how it decides to divvy stuff up. If you want to manually resize, you can do that, too.

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) outlines all the steps for that. It's the same in Dapper, just more point-and-click.

---

### Post by Moonshine on 2006-05-31
[QUOTE=aysiu]
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) outlines all the steps for that. It's the same in Dapper, just more point-and-click.[/QUOTE]

I looked through the website, but I just want to make sure I'm doing this right.

On the C: drive, or perhaps now i will call it hda1, theres only 15GB being used, with Windows XP. If I alter the size of that partition, to 40GB, which should give XP sufficien t room to move, and then create a partition after that space for Ubuntu, would that work? And I'd just like to make sure it wouldn't wreck XP when I'm modifying the partition size.

I've attached a screenshot to try and clear it up a little. 

[http://img151.imageshack.us/my.php?image=screenshot21ng.jpg](http://img151.imageshack.us/my.php?image=screenshot21ng.jpg)

Thankyou aysiu for your continued assistance, I'm very greatful. :)

---

### Post by aysiu on 2006-05-31
The best partitioning advice I can give is here:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

It looks as if you already have the mechanics of using the partitioning tool figured out. The only thing I'll say is that Windows XP likes to be at the beginning of the drive.

---

