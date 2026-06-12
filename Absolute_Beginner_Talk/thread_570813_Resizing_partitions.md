---
title: "Resizing partitions?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by foundation on 2007-10-08
So, I want to dedicate more space to Ubuntu so I'm going to take another 10GB from the XP partition and I was wandering the best way to go about this?

[img]http://img227.imageshack.us/img227/8411/partmagidisk1fi3.jpg[/img]

That's the current setup. I can resize the XP partition in PartitionMagic but I don't know if I'm able to resize the others. Also, if I resize the EXT3 one should I also extend the Extended/Linux Swap ones?

Thanks.

---

### Post by julian67 on 2007-10-08
1: Back up your data.

2: Make sure you have backed up your data.

3: see points 1 and 2

OK now you are bullet proof :) You could use Partition Magic and it will probably work OK but it is not what I would use on any disk that contains non MS filesystems. Occasionally it breaks the partition table. You could try a free alternative like [GParted-Live]("http://gparted.sourceforge.net/livecd.php") whose interface will feel quite familiar. It's a small download btw. 

You can use it broadly the same way as you would use Partition Magic. Resize/shrink  the XP partition then move/expand the Ubuntu partition to the left to fill in the space. Then apply the changes. You can leave the swap as is. I guess the whole process might take 20 minutes up to an hour depending on what CPU and RAM you have so be patient.

---

### Post by mivo on 2007-10-08
And don't forget to backup your data! :-D

---

### Post by Paqman on 2007-10-08
[Gparted](http://gparted.sourceforge.net/) can shrink your NTFS partition and grow your ext3 one. You don't need to touch your swap unless you change the amount of RAM you're using.

A good alternative to expanding your Linux root partition would be to create a new partition and mount your /home there. That way you can reinstall Linux whenever you like without losing all your settings or personal data.

Don't forget to back everything up before doing any resizing, either.

---

### Post by Shazaam on 2007-10-08
Did you back up your data? lol.
Also DEFRAG DEFRAG DEFRAG Windows before ANY resize.

---

### Post by HermanAB on 2007-10-08
Hmm, wait a minute.  The NTFS partition is before the / partition.  I don't think a partition can be made to grow backwards and still work.  So, either you have to use the freed space for something else such as /home or you may have to re-install Ubuntu.

So, backup abschlooly *everything*...

Cheers,

H.

---

### Post by julian67 on 2007-10-08
> **HermanAB said:**
> Hmm, wait a minute.  The NTFS partition is before the / partition.  I don't think a partition can be made to grow backwards and still work.  So, either you have to use the freed space for something else such as /home or you may have to re-install Ubuntu.

So, backup abschlooly *everything*...

Cheers,

H.

It should work with no problem. Recent versions of Gparted (for about a year) can grow a partition either way.

---

### Post by louieb on 2007-10-08
> **julian67 said:**
> 1: Back up your data.... [GParted-Live ...]("http://gparted.sourceforge.net/livecd.php") leave the swap as is. ...20 minutes up to an hour depending on what CPU and RAM you have so be patient.

Yes above all be patient 3GHz dual core cpu, gig of ram. 160 gig sata drive here. Took about 2 hours to move my Linux partition 30 gig to the left.

---

### Post by dz0004455 on 2007-10-08
it took me all day to redo the partion table on my drive, and btw ive never backed up before partioning a drive, no valuble data, but, ive never lost anything, so dont let that scare you away from it.

---

### Post by julian67 on 2007-10-08
> **dz0004455 said:**
> it took me all day to redo the partion table on my drive, and btw ive never backed up before partioning a drive, no valuble data, but, ive never lost anything, so dont let that scare you away from it.

I've had Partition Magic break a partiton table a few years ago (and seen plenty of help me posts from others in the same situation) and recently had a failure when using GParted to move and resize a large partition. But I have spare external drives and I *do* back up everything I value, which saved me from losing 10000 photographs. The hardware was fine btw, wiped it, reformatted, copied the backed up data across and all OK. I've also made the classic foobar of doing a disk clone of my home partition to a blank disk (to use in a different PC) but getting the direction a teeny ween little bit the wrong way round....result: 2 blank disks and a temporary state of brain numbness and the realisation that drinking 2 or 3 big bottles of Heineken is not ideal preparation for disk management. But I had a back up from only a week before and in an hour I was up and running after restoring it and re-downloading my mail from pop3 server and I guess I lost only some portions of p2p shares and a few bookmarks and saved web pages. 

There's a saying that there are 2 types of computer users; those who have suffered hard disk failure and those who are going to.

---

### Post by foundation on 2007-10-09
I forgot to back up. :(







Just kidding, thanks for the excellent replies, I think for now I might not try and mess with anything till my short trip is over so I don't have to frantically try and fix anything before I get on my flight tomorrow.

My temp solution is basically just to store the *large files* (Some movies, music, etc) on the NTFS partition since I finally went into XP (I hadn't in almost a week, just been using Gutsy) and shut it off properly so now the NTFS partition auto-mounts and I can just access the certain files. :)

.. but when I'm back I'm going to attempt it, hah. Thanks again all of you. :)

Last time I tried using GParted I remember it seeming to lack functionality or I simply wasn't able to do things I could in Partition Magic but I'll download the latest version and see how it is.. actually, on the 7.10 Live CD isn't there some form of GParted on there or am I mistaking it for some other basic partition program?

---

### Post by julian67 on 2007-10-09
> **foundation said:**
> 

Last time I tried using GParted I remember it seeming to lack functionality or I simply wasn't able to do things I could in Partition Magic but I'll download the latest version and see how it is.. actually, on the 7.10 Live CD isn't there some form of GParted on there or am I mistaking it for some other basic partition program?

I don't know about 7.10 but in 7.04 and earlier the version of GParted in the repos or in the distro has always been some way behind the current version. GParted got a lot more functional over the last year, you shouldn't find anything lacking in recent versions. If you do then you could look at Parted Magic which extends the functionality of GParted by having a lot of other tools on the CD. GParted also has other tools on CD but unfortunately they haven't found the need to ship with decent (any?) documentation whereas Parted Magic does. Fundamentally the same though.

---

