---
title: "If RAID 1 isn't for backup then ..."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by thornomad on 2007-02-11
I see a lot of people saying that "RAID 1 is not a backup system" -- even though there are two copies of your files and, in the event of hard disk failure, you should be able to recover them.  Reason given: if you were to write a corrupt file, it would be written to both RAID disks.  I get that.  

My question though is: what is a good backup system then?  I plan to use rsync.net to backup my important files (less than a GB worth of documents and financial stuff), but for the many many many GB of music and video that I have, are there any recommendations on how to set up a good redundant/backup system ?  Originally I was going to go with a RAID 1 system, but now I am worried that won't be good enough.

Is it better to use the two hard drives independently and create an rsync script to backup between them ?  Or another RAID system ? I just don't want to lose my music and videos if something were to happen but I don't want to pay for offsite backup for 100s GB of storage.

Thoughts?

Thanks!

---

### Post by John E on 2007-02-11
If it's only data files you're talking about, buy a second hard drive. Then zip up all your important files into a single zip or tar file and save it on the 2nd drive. Do this periodically (say once every week) so that you always have at least 2 backed-up copies of your data. With the backups on a completely separate drive you'd be very unlucky to lose both drives. Also, the idea behind having multiple backup copies is so that, if you suddenly notice a corrupted file, you've got several copies of it to choose from (therefore, if you unwittingly backed up a corrupted copy, hopefully you can go back a few weeks until you find an uncorrupted copy).

---

### Post by mcduck on 2007-02-11
Separate internal hard drive isn't safe, as failure in powersource or motherboard could still easily fry all your hard drives at once..

Best way is to use external hard drive, plug it in, do your backup, unplug it and put in some safe place.

---

### Post by John E on 2007-02-11
Yes - but unless you buy a SCSI card or NAS, any external hard drive is likely to be a low performer for a GB or more of data.

Actually, I use both methods. I make nightly copies to an internal hard drive (for speed) and then, about once every fortnight, I back up the whole partition to an external USB drive using Paragon Backup (under Windows, unfortunately).

---

### Post by thornomad on 2007-02-11
All right, thanks.  These are all great suggestions.  

I suspect if I use rsync with the external hard drive it shouldn't take as long (after the first sync); just the plugging it in and unplugging it bit that is a bit tedious.  I see what you mean though, in terms of preventing from a spike on the line or whatnot.

I plan to put in a gigabit ethernet router here someday soon; I suppose I could get an internal hard drive in a different box and have it backup to that.  Hmm.

The question becomes: how much is too much?  Smile.  Or is too much never enough.  

PS: these would be music/movie/pictures mostly; my data is going to be backed up offsite somewhere.

Thanks.

---

### Post by John E on 2007-02-11
> **thornomad said:**
> The question becomes: how much is too much?  Smile.  Or is too much never enough.
Well, that's a question that only you can answer. :)  The only advice I'd give you is to get the _slickest_ and _fastest_ solution you can afford. The reason being that, if your backup solution is inconvenient (or too slow) you'll find yourself using it a lot less often than you should - which of course, defeats the purpose.

---

### Post by thornomad on 2007-02-11
> **John E said:**
> The only advice I'd give you is to get the _slickest_ and _fastest_ solution you can afford. The reason being that, if your backup solution is inconvenient (or too slow) you'll find yourself using it a lot less often than you should - which of course, defeats the purpose.

Yea, that is an excellent point; and the reason I really wanted to make it an automated system entirely.  Currently I use SuperDuper! on my Mac and backup everything to an external hard drive ... but I never remember to do it and my backups are spread out much to far.

Was hoping to get a system of at least protecting my data in place that would serve me better.  First step is getting all the data on a Ubuntu File Server; next would be automating the backup process.

---

### Post by vgrisham on 2007-02-11
> **mcduck said:**
> Separate internal hard drive isn't safe, as failure in powersource or motherboard could still easily fry all your hard drives at once..

Best way is to use external hard drive, plug it in, do your backup, unplug it and put in some safe place.

I disagree (to an extent). RAID 1 has saved my OS twice in the last five years. The odds of losing one hard drive are much greater than frying two at once. RAID 1 gives you time to try to salvage your installation in addition to the files you create between backups.

Having said that, RAID is not a substitute for regular backups of your user files. RAID simply gives you another option when disaster strikes, and it's an option that can save you hours of reinstallation woes (especially since so much effort has to be put into configuring linux to your needs). 

Backing up regularly is a safety net for your critical files. RAID is a safety net for your operating system.

---

### Post by thornomad on 2007-02-13
Yea ... I think what I would like to do is have a RAID 1 setup and then do data backups to an external disk.  Do those less frequently but keep the disk unplugged when not in use.  That probably will be safest (and most reliable) for me.

D

---

