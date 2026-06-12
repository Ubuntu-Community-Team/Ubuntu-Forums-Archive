---
title: "semi-complicated partitioning/reinstall questions"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by fhqwhgads on 2006-06-03
Hi, first post.

I've been using Dapper for a couple weeks now, it's absolutlely great. I've only booted to XP a couple times since I installed Ubuntu. I'm now at the point where I've decided that Ubuntu Dapper is the OS I want to use in my daily life, so I want to reconfigure my hard drive partitions as efficiently possible. I need XP available to run a DAW and provide support for others trying to do the same (that's part of my job).  

Up to now, my Ubuntu install has basically been a sandbox where I tried out all kinds of apps and stuff I found interesting. Most was good, some... not so much... I have no problem blowing it away and starting fresh, in fact I think this would be ideal for stability purposes. But maybe that's older XPeriences talking. ](*,) 

This leads me to question one: **Is there an easy way to back up and restore my firefox and thunderbird data?** Mostly I'm concerened about cookies and bookmarks in firefox, all mail and addresses in thunderbird (note that this is Ubuntu to Ubuntu, not XP to Ubuntu... I already had that headache).

My plan is to basically reformat the 100GB hard drive in my laptop (ASUS z71v), install XP to partition 1 and not much else besides my Samplitude DAW software. I really don't care if it's NTFS or FAT, and I think 10-15GB should be sufficient. Anyone have thoughts on this?

Next, I'd boot to the Dapper disc, to start partitioning the rest of the hard drive. Here's the rub: I want a smallish partition for Ubuntu too, because I need (want?) a huge home partition (for media files and sometimes a Samplitude project created under XP) to be read- and writable by both XP and Ubuntu. 

FAT is limited to 32gb, right? I've read that this limit can be bypassed with Win98 tools, but is this a good idea? Alternatively, I've seen some tools that claim to offer EXT support to XP ([Ext2Fsd]("http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd") is one). **Can anyone confirm or deny that either of these methods are working?**

So here's a mockup of the partitioning scheme:

1 - primary - ntfs - hda1 - Windows XP - 15GB
2 - primary - ext3 - hda2 - Ubuntu Dapper - 5GB
3 - primary - ext3 - hda3 - Edgy Eft - 5GB (for playing around, just thinking ahead)
4 - extended - n/a - hda4 - rest (mount point)
5 - logical - swap - hda5 - swap space - 1GB
6 - logical - **???** - hda6 - /home - 75GB (roughly)

**Does this look good? Can you suggest something better? How can I use the home directory from XP without much trouble? Should I set all this up with the Gparted boot disk before reinstalling XP?**

---

### Post by az on 2006-06-03
[QUOTE=fhqwhgads]
This leads me to question one: **Is there an easy way to back up and restore my firefox and thunderbird data?** Mostly I'm concerened about cookies and bookmarks in firefox, all mail and addresses in thunderbird (note that this is Ubuntu to Ubuntu, not XP to Ubuntu... I already had that headache).
[/QUOTE]

You can export all those.

---

### Post by fhqwhgads on 2006-06-03
[QUOTE=azz]You can export all those.[/QUOTE]Thanks. I found this [here]("http://www.hddsaver.com/content/16/index.html"):
> /home/*username*/.mozilla-thunderbird/xxxxxx.default/Mail/Local Folders

Inside this folder the is raw data for your emails. All you have to do to back up the emails is to save this folder in a secure location. Restoring the emails is a matter of dropping the saved folder into a chosen profile.
Seems this is the way to go for tbird, I guess firefox would be the same? In any event, sure, it's easy to export bookmarks... as for cookies and saved logins.... well, I can't find a way inside firefox.

---

### Post by ubuntuben on 2006-06-03
What I try to do is set up a separate partition to use for the home directory. In my experience, I've been able to reinstall the system and keep all of my user files intact without having to reinstall them. When I install another system or do a reinstall, I just direct the installer to use the partition I had set aside for /home.

---

### Post by fhqwhgads on 2006-06-03
Right, that's the plan, as I've detailed in post 1. Do you have any advice as to how that should be formatted for use with either OS?

---

### Post by Mustard on 2006-06-03
[QUOTE=fhqwhgads]Right, that's the plan, as I've detailed in post 1. Do you have any advice as to how that should be formatted for use with either OS?[/QUOTE]

You probably want the 75 Gb 'home' partition to be ext3 as well, as vfat is not a great choice, as it doesnt support permissions/ownership.  I believe there is a some software that you can get for windows that gives read/write ext2/3 support, so that would be something to look into.

[http://ext2fsd.sourceforge.net/index.htm](http://ext2fsd.sourceforge.net/index.htm)
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

Looking in google I can find stuff that supports reading of ext2/ext3 and writing of ext2.  I thought there was something out there for ext3 write support in windows, although I may be wrong.

I'd be tempted to break the 75 Gb partition up again and have a healthy size home partition of say 10 or 20 Gigs, and then assign the rest to a 'storage' partition, which could be fat32.  The advantage of this I would think is it easier to back up your /home partition if you don't actually store all your large media files in the /home folder, as they make the backup size huge! :)

---

### Post by fhqwhgads on 2006-06-03
Thanks Mustard!
[QUOTE=Mustard][http://ext2fsd.sourceforge.net/index.htm](http://ext2fsd.sourceforge.net/index.htm)
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)[/QUOTE]
Here's another one I found recommended in a forum member's sig: [http://www.fs-driver.org/](http://www.fs-driver.org/) 

Does anyone have experience with any of these?
[QUOTE=Mustard]
I'd be tempted to break the 75 Gb partition up again and have a healthy size home partition of say 10 or 20 Gigs, and then assign the rest to a 'storage' partition, which could be fat32.  The advantage of this I would think is it easier to back up your /home partition if you don't actually store all your large media files in the /home folder, as they make the backup size huge! :)[/QUOTE]
Yeah, except FAT32 is still limited to 32GB, hence my wanting to stay with one giant EXT2 partition. I plan to use an external USB drive formatted in EXT2 for differential backups, shouldn't be too ugly.

---

### Post by Mustard on 2006-06-03
[QUOTE=fhqwhgads]Here's another one I found recommended in a forum member's sig: [http://www.fs-driver.org/](http://www.fs-driver.org/) [/QUOTE]
Ah..thats the one I couldn't find with my search. :)  I've seen that one recommeded a few times, but never used it myself.

---

### Post by catlett on 2006-06-03
[QUOTE=Mustard]Ah..thats the one I couldn't find with my search. :)  I've seen that one recommeded a few times, but never used it myself.[/QUOTE]
That driver works well. I haven't had any issues but I don't do much cross writing/reading. The few occasions I have used it there haven't been any issues with how the data changes are saved.
It is very easy to use. After you install it their will be an icon in the "control panel" in windows. (it's easiest to find when you enable "classic view") When you enter the application you will view your hard drive similar to hoiw you see it in partitioning applications. Your windows partition and any fat32 partitions will have a drive letter, the linux partitions won't.
What the linux partitions have is a drop down menu in it's section. The menu has a list of available drive letters. Choose a drive leter and when you exit the linux partition is in "my computer" next to your local disk C with an icon and whatever drive letter you have.
From there you just double click like any other icon to explore the partition and you open whatever file type you want with the applicable window's application.

---

### Post by fhqwhgads on 2006-06-03
Thanks for the help, I'm gonna go ahead and take a crack at it now.

---

### Post by Mustard on 2006-06-03
[QUOTE=fhqwhgads]Thanks for the help, I'm gonna go ahead and take a crack at it now.[/QUOTE]
Good luck. :)

---

### Post by steve.horsley on 2006-06-03
I would crate an archive of the directories in question like this:
> tar cvf thunderbird.tar .mozilla-thunderbird
Then you can copy these tar files to a USB stick or somewhere else safe until you can replace it in your new home folder with
> tar xvfp thunderbird.tar

---

### Post by fhqwhgads on 2006-06-03
That's pretty much what I did, albeit graphically. Worked like a charm. Now to get my XP drivers downloaded... it didn't detect hardware nearly as well as ubuntu.:rolleyes:

---

