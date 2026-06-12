---
title: "Had Disc Space"
date: 2007-05-20
forum: Apple Intel Users
---

### Post by dareofficer on 2007-05-20
Hello, I have installed Ubuntu 7.04 on my Intel Mac iMac 20".  I love it so much, I should have picked to split the hard drive.  I only selected 32gb for Ubuntu.  Is there a way to make it split now?  Or will I have to re-do it all again??

Also my graphics should be 1680x1050, but it is only 1400x1050, it is a ATI chip on the iMac.  Can I get that fixed as well?

Thanks!!

---

### Post by ronocdh on 2007-05-21
Regarding the partition, I don't quite understand what you want to do. Are you trying to give Ubuntu more space? Less space? Either way try using iPartition. It's friendly to HFS+ and can jerk partitions around nondestructively. It's pretty sweet.

For the ATI problem, have you tried these?```
sudo apt-get install xorg-driver-fglrx
```and```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Good luck, and post back if you need clarification.

---

### Post by dareofficer on 2007-05-21
I got the video going thanks.

Yes, I want to expand the hard drive.  It is setup with only 32gb for Linux.  I want to keep osx, but expand the linux side.  Is this possible?

---

### Post by ronocdh on 2007-05-21
> **dareofficer said:**
> I got the video going thanks.

Yes, I want to expand the hard drive.  It is setup with only 32gb for Linux.  I want to keep osx, but expand the linux side.  Is this possible?
[iPartition]("http://www.versiontracker.com/dyn/moreinfo/macosx/23828") is probably your best bet in this regard, assuming you are not interested in reinstalling Linux. I've heard very positive things about it (search for it in this forum), but honestly have never used it myself. So back up your data and please remember to post back with results! =)

---

### Post by dareofficer on 2007-05-21
I was able to create another extended part.  It is not part of my linux install part.  Can I move my home directory to the new part?  I'm part way there at least.  I just want to be able to install any new software to the new part.  This might be good in the event I have to re-install my software is on that part and not the part where the install is.

Thanks

---

### Post by ronocdh on 2007-05-21
> **dareofficer said:**
> I was able to create another extended part.  It is not part of my linux install part.  Can I move my home directory to the new part?  I'm part way there at least.  I just want to be able to install any new software to the new part.  This might be good in the event I have to re-install my software is on that part and not the part where the install is.

Thanks
Hm, I don't know whether this is possible, though theoretically anything is in Linux, right? ;) You may want to read up on the [**chroot**]("http://en.wikipedia.org/wiki/Chroot") command, as it sounds like a similar process to me, but I don't know how far it will get you.

With a free and presumably spacious new partition, why not just save all your media there? That way if you ever need to reformat/reinstall Ubuntu, you'll be wiping only the partition with your system on it, and none of your personal files will be lost. Also, if this additional partition is formatted to something like FAT32, you can share it amongst all OSes you may have. (This is still possible with ext3 with installable filesystems, and in fact I prefer the latter method.)

---

### Post by benanzo on 2007-05-21
How many partitions do you currently have?  If you installed OS X first then you will have a 200MB EFI (fat32) partition at the beginning of the disk and the OS X parition will be second and then Ubuntu.  Are you wanting to shrink the OS X partition to make more room for Ubuntu?  I would suggest creating a tarball out of your Ubuntu system and saving it to an external disk or DVD, then booting into the LiveCD and deleting the current Ubuntu partition and shrinking the OS X partition, then creating a new ext3 partition with the free space and just restoring your Ubuntu tarball to the new partition.

A good guide on how to backup your installation:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

This method requires a few steps but at least you wont have to reinstall from scratch.

---

### Post by dareofficer on 2007-05-22
Thanks for the help with this.

Yes, OSX is on first.  Yes, I want to shrink OSX, and expand Ubuntu.  I was able to do that, however I now have 3 parts instead of two.  I don't mind keeping the new part, if I can install all my sofware there?  I would also like to make my home folder there, is that possible?  When installing software is there a way to have it do that automatic?

Thanks

---

### Post by ronocdh on 2007-05-22
> **dareofficer said:**
> Thanks for the help with this.

Yes, OSX is on first.  Yes, I want to shrink OSX, and expand Ubuntu.  I was able to do that, however I now have 3 parts instead of two.  I don't mind keeping the new part, if I can install all my sofware there?  I would also like to make my home folder there, is that possible?  When installing software is there a way to have it do that automatic?

Thanks
I don't really understand the motivation to install software to a different partition. Applications really don't take up that much room. Sorry for being repetitive, but I find it much more useful to save my media to partition separate from the installation; it's been vastly beneficial in times of reformatting, because I know my data is always safe in that it's elsewhere.

---

### Post by dareofficer on 2007-05-22
I'm somewhat still new to Linux.  Thanks, I'll keep it this way.  I would like to use a program Final Cut Pro like.  I could store the DV to the other hard drive.  I can put my MP3's there as well.

I have had Ubuntu on a PC before, but my Mac looks the best.  I'm very happy with it on my core2duo.

Thanks again for the help.

---

### Post by oskarloko on 2007-05-23
I also recommend you to use one partition for each OS you want to install and other one to share data ( music, video, personal documents, sharing data folders ) within each OS.

You can make a clean repartition by erasing all disk **( renember to backup all your apps and your data )**

Pros
[LIST]
[*]You now have a backup of all what you need
[*]Can make a data / apps cleaning
[*]Planning it with care, you can set your HDD partitions very usefull
[*]Learn a lot!!
[/LIST]

Cons: 
[LIST]
[*]Forgetting something to save
[*]It'll consume a evening...
[*](very rare) get stuck on installation
[/LIST]

Only  one question, if anyone have reinstalled MacOsX before... ¿ which is the minimal size of this OS ? 
If you install fresh OSX with no programs nor data ( only a basic system and update)

For my experience:
[LIST]
[*]Ubuntu fresh install: 3-5Gb
[*]Ubuntu when I download every app / package / utility I use: 5-7Gb
[/LIST]

(maybe same for Windows... )


What do you think ?


I forgot to tell !!
On rEFIt web, there's said that the first 200Mb FAT32 partition is not needed... except *maybe *for firmware updates... 
200Mb is not very much space, but a partition *'slot'* is a good resource ( on MBR/EFI systems, more important !! )

---

### Post by Seamyst on 2007-05-23
I just wiped everything clean and started again last week.  I gave Tiger a 10-gig partition, since I wasn't sure what the minimum install size was and I wanted to have room for updates and such.  I believe I installed Tiger with just my printer drivers and Photo Booth (because it's fun), and no foreign languages or other programs or anything.  I also used **Monolingual** to remove roughly 300 megs' worth of foreign-language stuff after updates were done.  It took 2-3 gigs total, then tack on another half a gig or so for updates.

So, yeah, bare-bones Tiger install:
[LIST]
[*]2-3 gigs
[/LIST]

I imagine 10.2.x would take about the same amount of space, maybe a little less.

**ETA:**  I'd recommend giving OS X 7-10 gigs for the partition - that'll keep it from complaining that it doesn't have enough space for updates, and it gives you enough room to work in if Ubuntu has any problems.  Plus it still gives you plenty of space for Ubuntu and a shared partition if you want one.

---

### Post by ronocdh on 2007-05-23
**ETA:**  I'd recommend giving OS X 7-10 gigs for the partition - that'll keep it from complaining that it doesn't have enough space for updates, and it gives you enough room to work in if Ubuntu has any problems.  Plus it still gives you plenty of space for Ubuntu and a shared partition if you want one.[/QUOTE]
Agreed. Even 10GB is still *maybe* 10% of your drive space, so it's really not that big of a deal IMO, and a workable OS X partition has saved me countless times already on occasions when Ubuntu was acting, well, edgy or feisty!

As for the partition for filesharing/media, I'd consider using ext3 over FAT32; it doesn't fragment nearly as badly, and OS X and r/w with it through the use of installable FSes. Very handy.

---

### Post by oskarloko on 2007-05-28
.... with a triple boot 80Gb HDD Macbook, I'll wip al and make

12Gb for each OS ( 2Gb for swap as I've 1Gb of RAM )

Rest for filesharing... ¿ FAT32 or ext3 ?

> As for the partition for filesharing/media, I'd consider using ext3 over FAT32; it doesn't fragment nearly as badly, and OS X and r/w with it through the use of installable FSes. Very handy.
¿ How ?

I used [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) for MacOS, but that was a pain...


(Maybe I'm very off-topic ??)

---

### Post by ronocdh on 2007-05-29
> **oskarloko said:**
> 
¿ How ?

I used [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) for MacOS, but that was a pain...


(Maybe I'm very off-topic ??)
This is exactly what I was referring to; I apologize for not linking directly. Are you using Tiger? My performance with this module has been stellar: full r/w to my Ubuntu partition on my MBP as well as full r/w on several external hard drives (Firewire and USB) which I share among many machines.

I even the external drives on a Windows XP box at home! I haven't tested this, because I so rarely use WinXP on my laptop, but that installation should be able to read to my Ubuntu partition. I know that in WinXP on my tower at home, it *can* read the Ubuntu party there. =)

---

### Post by oskarloko on 2007-05-30
Ah, I was wondering if you used ext2fxs or MacFUse

[http://code.google.com/p/macfuse/](http://code.google.com/p/macfuse/)
[http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)
[http://sourceforge.net/projects/ext2fuse](http://sourceforge.net/projects/ext2fuse)

¿ Which version of ext2fsx have you used ( 1.3 or 1.4d4 ) ?
( I've a little trouble with last one )

¿ Has anybody tried to reinstall ALL without EFI partition ?

---

