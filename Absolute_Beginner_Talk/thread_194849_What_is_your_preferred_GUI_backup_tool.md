---
title: "What is your preferred GUI backup tool?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-12
Hi,

I am interested to know what your favourite GUI backup program is.

When I used XP Pro I used Ghost.

Thanks.

---

### Post by r3st on 2006-06-12
i use Baxit Up

---

### Post by elemental666 on 2006-06-12
you know you can still use ghost right?

---

### Post by u.b.u.n.t.u on 2006-06-12
[QUOTE=elemental666]you know you can still use ghost right?[/QUOTE]

Ghost for Linux ?
[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

---

### Post by u.b.u.n.t.u on 2006-06-12
[QUOTE=r3st]i use Baxit Up[/QUOTE]

Do you have a url for that?

---

### Post by elemental666 on 2006-06-12
well, when I purchased ghost (ver 9 I think) I got 2 cds, one that installs all the stuff you see in winXP, the other is a bootable image maker, it works independant of the os.  You chose the partitions from a textbased menu system and it will prompt you to instert blank media.  I'll have to wait till I get home to get more specific.

---

### Post by r3st on 2006-06-12
[QUOTE=u.b.u.n.t.u]Do you have a url for that?[/QUOTE]

my friend made it
i dont think he has released it yet tho

---

### Post by u.b.u.n.t.u on 2006-06-12
I didn't know that. Thanks. I've used Ghost for years. I don't recommend version 10 though. The interface has changed a lot, making it better suited for scheduled tasks rather than an occasional manual use.

I'll try the gnu gpl software first. 

I feel my data is a lot safer now that I am using ubuntu.

---

### Post by matthew on 2006-06-12
Install the package called sbackup. It will put two packages in your System->Administration menu, one called Simple Backup Config and a second called Simle Backup Restore. It's easy to use and works well and was a Google Summer of Code project last year.

---

### Post by u.b.u.n.t.u on 2006-06-12
[QUOTE=matthew]Install the package called sbackup. It will put two packages in your System->Administration menu, one called Simple Backup Config and a second called Simle Backup Restore. It's easy to use and works well and was a Google Summer of Code project last year.[/QUOTE]

Thanks.

Screenshot
[http://sbackup.sourceforge.net/ScreenShots](http://sbackup.sourceforge.net/ScreenShots)

By the way, their website, one page, is filled with a great many pornography links, which is a worry.

Anyway I used synaptic to install it. This program is a backup tool, but not a HDD image maker. It looks good.

---

### Post by matthew on 2006-06-12
[quote=u.b.u.n.t.u]Thanks.

Screenshot
[http://sbackup.sourceforge.net/ScreenShots]("http://sbackup.sourceforge.net/ScreenShots")

By the way, their website, one page, is filled with a great many pornography links, which is a worry.

Anyway I used synaptic to install it. This program is a backup tool, but not a HDD image maker. It looks good.[/quote]I hadn't seen their web page, but it's a wiki that has been defaced by vandals...hence the links you mentioned. Sorry about that. It's a good program, although you are right, it won't make a disk image.

Note to self: read the original post better in the future before responding with only marginally helpful recommendations. :)

---

### Post by elemental666 on 2006-06-12
So I was looking through the ghost user manuals online and I don't think the ver9 or ver2003 disk will work quite like I thought they would...  Ver 10 says it supports ext2, ext3 and swap fs.

However, I did find these native linux apps:

[partimage]("http://www.partimage.org/Main_Page") and [SystemRescueCd]("http://www.sysresccd.org/Main_Page") which is a live cd that has partimage on it...

and [Ghost 4 Linux]("http://freshmeat.net/projects/g4l/")

and [mondo]("http://www.mondorescue.org/")

beyond that there is this recently updated howto: [http://tldp.org/HOWTO/Linux-Complete-Backup-and-Recovery-HOWTO/index.html](http://tldp.org/HOWTO/Linux-Complete-Backup-and-Recovery-HOWTO/index.html)

---

### Post by u.b.u.n.t.u on 2006-06-12
matthew, yeah it isn't cool vandals defacing their page like that.

elemental666, thanks for those suggestions. I've bookmarked them for later. They look interesting.

I don't think a HDD image of ubuntu is as important as it is for XP. ubuntu is much faster and easier to install and set up than XP. It also feels more secure and therefore less likely to need to be re-imaged anytime soon.

I'll test those image makers in the near future and may add my view on them to this post, which may assist others searching and finding this thread.

Cheers.

---

### Post by elemental666 on 2006-06-12
both mondo and partimage are in the ubuntu dapper repos...

I'm gonna give partimage a go first, will report...

EDIT:

partimage can't backup a mounted partition, so I guess I have to be on a live cd environment or do it over the network... moving on to SystemRescueCd, since it has partimage on it :D


SystemRescueCd, as far as making the image is concerned, it was a snap.  Burn the iso, reboot, you get booted into a LiveCD shell, create and mount the destination (I backed up to a partion on my 2nd HD), run partimage, select the partition you want to image, give it a destination path and filename, select a few other options, like gzip or bzip2, etc.  and away she goes, took about 10 minutes all told, to back up a fresh Ubuntu Dapper install after updating the kernel (k7) and all packages.  It packed 2.1G of data into an image that was slighty over 800M.  only drawback so far is having to reboot everytime I need to make a back up. now to test it out, I'm goona install a bunch of software and check the df -v for the partition.  Then restore and check it again.  Should be missing the apps and have 2.1G used.

EDIT:

SystemRescueCd worked like a charm, after install automatix and selecting everything in the list, the drive had 2.3G data.  Reboot, restore, back to 2.1G,  reboot, got into gnome. None of the automatix installed apps, or automatix are present.

Phase2 testing: rebooted into live environment, and mounted the backed up partition, ran rm -rf * from that partitions root. Restore, reboot, back into gnome, with out a hitch.


While I was doing all that I kinda looked over the Mondo stuff and its looks to be somewhat complicated, at least to the novice.  However it does look like it could be a better solution.  As it is, I'll be using this system rescue as a backup solution (might as well find out what else its useful for while I'm at it, huh!).

partimage was extremely intuitive, fast and offers GREAT compression (I used gzip, bzip2 would have gained further compression).  Its only 123ish MB so on a cd that leaves you about 500-650ish MB, which may be room enough to put a bzip2'd image of a base Ubuntu install (once you trim the fat and all).  I whole heartedly recommend the system rescue cd image linked above.

Have phuz!

---

### Post by u.b.u.n.t.u on 2006-06-12
elemental666, excellent reviews!

:D

---

### Post by elemental666 on 2006-06-12
done and done, edits to the previous post.

I'll use partimage on the rescue cd until I get the network file sharing setup on my desktop and laptop.  Then I can back up one machine to the other and store the images on my external drive or burn them to cd.  I'll continue to use this solution until I have time to tinker with Mondo.

---

### Post by u.b.u.n.t.u on 2006-06-12
I'll follow your recommendation, partimage it is. Thanks again.

---

