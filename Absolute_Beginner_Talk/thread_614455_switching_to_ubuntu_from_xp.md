---
title: "switching to ubuntu from xp"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by twinscroll on 2007-11-16
Ok, I have been reading up on making the change to ubuntu from XP. I dont think I will have any hardware issues, and I think that I have identified all the programs that I will need. And I even think that I may be able to get WoW to work with a little effort. 

I have a Gateway laptop, which I havent really found any issues with for anyone. The only sticking point that I have right now is that I only have one PC. All of my music, documents, videos, etc, are on my hard drive. This is the only thing that I can think of doing. 

I have enough room on my hard drive to install Ubuntu and dual boot XP. I do want to go full Ubuntu and force myself to get used to Linux, so dual booting is not a permanent solution. How do I move all of my files from an XP partition to a Linux partition? How can I resize my partitions from Ubuntu once fill up the existing partition in Ubuntu? I really don't want to burn all of my info to DVD's, I just don't have that many DVD's :) 

Am I on the right track here? Or is there a better way to do this? Keep in mind, I only have one PC. 

Thanks in advance!

---

### Post by rexxxlo on 2007-11-16
do you have an external usb hdd?

move the files to that and then after ubuntu is installed go grab them from the external drive.

---

### Post by ramjet_1953 on 2007-11-16
Yes, there are plenty of posts on these forums on dual-booting and using gpated to re-size partitions.

Providing you back-up your data and follow instructions, you shouldn't have any problems.

Another solution would be to buy another hard drive.

They are relatively inexpensive these days and this way, your precious data is isolated and you can play to your heart's content with Ubuntu.

If you are using a tower system, you can even get a caddy system, that allows you to plug and unplug your hard drive, using a drive bay.

Regards,
Roger :cool:

---

### Post by Inxsible on 2007-11-16
you can transfer all your data to an external drive, install ubuntu and then re-transfer them.
if that is not a viable option, you can dual boot making sure that all you data is in the XP partition. Then after ubuntu is installed, you can transfer the data to ubuntu and then format the XP partitions (that way you will be able to get rid of XP) which is what you want right ?

Ubuntu can read and write to NTFS partitions out of the box (since 7.10) so it wont be a problem

---

### Post by twinscroll on 2007-11-16
I think I might go ahead and get an extenal HDD. I didn't realize that they had came down in price so much. $80 on newegg for a 250GB drive. Not bad. But, I think that after I back up my info to USB HDD I will go ahead and play around with transfering files between partitions and then resizing the partitions from Ubuntu, just for the experience :D

---

### Post by Inxsible on 2007-11-16
> **twinscroll said:**
> I think I might go ahead and get an extenal HDD. I didn't realize that they had came down in price so much. $80 on newegg for a 250GB drive. Not bad. But, I think that after I back up my info to USB HDD I will go ahead and play around with transfering files between partitions and then resizing the partitions from Ubuntu, just for the experience :D
If you look hard enough, you can also find a 500GB for 100-120 odd bucks !!

Good Luck !

---

### Post by wlc3069 on 2007-11-16
> **twinscroll said:**
> I think I might go ahead and get an extenal HDD. I didn't realize that they had came down in price so much. $80 on newegg for a 250GB drive. Not bad. But, I think that after I back up my info to USB HDD I will go ahead and play around with transfering files between partitions and then resizing the partitions from Ubuntu, just for the experience :D

i did the same thing when i switched to ubuntu from xp, and it was well worth the experience

---

### Post by SunnyRabbiera on 2007-11-16
as a suggestion get a seagate as they are usually very good externals with linux...
they dont use any odd firmware.

---

### Post by twinscroll on 2007-11-16
thanks for the feedback everyone! I am glad everyone is so helpful even with a newb such as myself :) I am excited to start using Linux finally!

---

### Post by newlinux on 2007-11-16
If you get a new external hard drive and you plan on using Linux primarily I would reformat it to ext3 or XFS before loading files on it. It will probably come NTFS. If you are planning putting a lot of large media files on it I recommend XFS over ext3.

---

### Post by rexxxlo on 2007-11-16
> **newlinux said:**
> If you get a new external hard drive and you plan on using Linux primarily I would reformat it to ext3 or XFS before loading files on it. It will probably come NTFS. If you are planning putting a lot of large media files on it I recommend XFS over ext3.

what is a large file? 4-5 gig? like a dvd backup ?

why xfs over ext3 and what are the differences?

---

### Post by TadH on 2007-11-16
> **twinscroll said:**
> I think I might go ahead and get an extenal HDD. I didn't realize that they had came down in price so much. $80 on newegg for a 250GB drive. Not bad. But, I think that after I back up my info to USB HDD I will go ahead and play around with transfering files between partitions and then resizing the partitions from Ubuntu, just for the experience :D

good luck ;0

---

### Post by newlinux on 2007-11-16
> **rexxxlo said:**
> what is a large file? 4-5 gig? like a dvd backup ?

why xfs over ext3 and what are the differences?

Yeah, that's on the larger side. It's a faster file system, and much better at dealing with large files (less fragmentation, quicker deletes, faster journal recovery) than ext3. It also uses 64-bit addressing. One downside is that XFS filesystems can't shrink, but they can enlarge.

That's why many people with mythtv installations use xfs for storage of their recordings.

---

### Post by rexxxlo on 2007-11-16
> **newlinux said:**
> Yeah, that's on the larger side. It's a faster file system, and much better at dealing with large files (less fragmentation, quicker deletes, faster journal recovery) than ext3. It also uses 64-bit addressing. One downside is that XFS filesystems can't shrink, but they can enlarge.

That's why many people with mythtv installations use xfs for storage of their recordings.

i have tons of media almost a tib deleted almost 250 gigs to clean a drive for ubuntu and i have a 64 bit processor and am currently running ubuntu 64bit 

would this xfs file system be a good idea for me it is mostly movies there is about 160 gigs of music 

when you say it cant shrink but it can enlarge what does that mean ?

---

### Post by newlinux on 2007-11-16
> **rexxxlo said:**
> i have tons of media almost a tib deleted almost 250 gigs to clean a drive for ubuntu and i have a 64 bit processor and am currently running ubuntu 64bit 

would this xfs file system be a good idea for me it is mostly movies there is about 160 gigs of music 

when you say it cant shrink but it can enlarge what does that mean ?

Yes, I think it would be good for you. What I mean by it can enlarge but not shrink is that if you set up a 150GB partition, you can't shrink it to 100GB even if there are 50GB free. You'd have to backup the data on it, destroy the partition, and then make a new 150GB partition and restore the data. But you can make it larger than 150GB without doing that. This not a concern for most people.

IF you want to format XFS you'll need to install xfsprogs from the repos.

[http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS) for more info on XFS (technical info).
Compare with: [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

