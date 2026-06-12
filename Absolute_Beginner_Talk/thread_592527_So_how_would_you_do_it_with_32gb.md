---
title: "So how would you do it with 32gb?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by zakeen on 2007-10-26
So Im doing the complete switch now to Ubuntu. I have a 32gb SSD drive and want Ubuntu only. Would you make the whole drive for Ubuntu or 8gig for the operating system and then 24gig for music, docs, movies. 

How would you guys go about it?

---

### Post by maybeway36 on 2007-10-26
I've never needed much hard drive space for the OS. I think I have 8GB out of 80GB for it now. 1GB for FreeDOS, and the rest for /home. None of the partitions are anywhere near filled up.

---

### Post by az on 2007-10-26
> **zakeen said:**
> So Im doing the complete switch now to Ubuntu. I have a 32gb SSD drive and want Ubuntu only. Would you make the whole drive for Ubuntu or 8gig for the operating system and then 24gig for music, docs, movies. 

How would you guys go about it?

If Ubuntu is the only OS on the system, why a separate partition?

Just put everything on one partition.  It's not like it's safer to create a separate partition - you're not protected from hardware failure...

---

### Post by evilregis on 2007-10-26
He may not be protected from hardware failure but it sure is easier to have a /home partition if he wants/has to to reinstall his OS at a later time.

---

### Post by zakeen on 2007-10-26
> **evilregis said:**
> He may not be protected from hardware failure but it sure is easier to have a /home partition if he wants/has to to reinstall his OS at a later time.

This is why I normally do it. I guess its from having a laptop and the only real way of fixing windows was to do a recovery. Having my important stuff on a different partition means I dont need to worry.

So is 8gb enough? leave the rest for /home?

what do you think?

thanks.

---

### Post by ThrobbingBrain66 on 2007-10-26
I typcially use 5GB for /

I've never filled it up, but I don't ever have tons of packages installed at one time.  I'd say 8GB is plenty.

---

### Post by LowSky on 2007-10-26
My solution

5Gb for / (root)
1Gb for swap
the rest for /home

---

### Post by zakeen on 2007-10-26
8GB it is then. Thanks, Now I will install 7.10

Im going down, wish me luck!

---

### Post by az on 2007-10-26
> **evilregis said:**
> He may not be protected from hardware failure but it sure is easier to have a /home partition if he wants/has to to reinstall his OS at a later time.

Not really.  Many problems are solved by dumping your home folder configs (create a new user).

And it's easier to just backup your stuff to external media - safer, too.

Not to mention the issue of running out of space.  If everything is on one partition, you share all the space.  If you keep separate partitions, you run more of a risk of filling one up and having to either move your partitions around (which is not often possible with a full drive) or just starting over from scratch.

---

### Post by Denn1s on 2007-10-26
5 or 8gb should be more than enought for your /, having /home in a separate partition is very usefull and yes its safer, root partition could crash leavin you the only choice to reinstall, but your data and configuration are somewere else so its no big deal

---

### Post by az on 2007-10-26
> **Denn1s said:**
> 5 or 8gb should be more than enought for your /, having /home in a separate partition is very usefull and yes its safer, root partition could crash leavin you the only choice to reinstall, but your data and configuration are somewere else so its no big deal

A "root partition crash" could mean a few things
1- hardware failure.  You are not protected from this by keeping a separate partition.
2- Filesystem corruption.  It's unlikely that a filesystem corruption will result in the whole filesystem going down.  You usually would be able to boot a live cd and salvage the remaining files - just the same as if you would have had many partitions.  Again, by keeping separate partitions you are not protected from this.  

Why would it be smart to reinstall on a failed drive anyway?

---

### Post by Seq on 2007-10-26
> **az said:**
> Not really.  Many problems are solved by dumping your home folder configs (create a new user).

This is rare in my experience

> **az said:**
> And it's easier to just backup your stuff to external media - safer, too.

This is not an issue of redundancy, but an issue of manageability. If one uses multiple partitions to avoid data loss, they are fooling themselves. As a matter of safety, redundant external backups are the only serious way to go.

> **az said:**
> Not to mention the issue of running out of space.  If everything is on one partition, you share all the space.  If you keep separate partitions, you run more of a risk of filling one up and having to either move your partitions around (which is not often possible with a full drive) or just starting over from scratch.

I run 8GB / on all my machines, and different size /home depending on drive, machine purpose. For example, my home server has 50GB /home, and another 50ish GB unallocated for further use later if needed. I don't understand why everybody must immediately allocate 100% of their disk when actual utilization is around 20%. Who knows where the rest would be useful. If I was to do it again, I'd use LVM here as it would solve the resizing/moving partitions issue.

My laptop just has two plain partitions. I never bother upgrading ubuntu versions as I usually had to do a bunch of hacks to get things working before (suspend fixes, weird config changes, etc etc) that I want to ensure are eliminated so I can start from a 'clean slate'. When installing, have it format / and not /home, and everything is dandy when it comes back up.

---

### Post by Can+~ on 2007-10-26
The /home+/+swap combo usually works well for switching, but as az said, there may be problems with user files within it. As everything in life, there are pros and cons. My solution is:

-Have the whole / and /home in one partition, aka a normal install.
-Have a small backup partition "for the next update", but mounted like in media. So when you are reinstalling the whole system, you move your beloved files there, and reinstall in the other partition.
-OR just use a DVD, pendrive, or external HDD.

*little offtopic* How fast is a SS Disk? =D

---

### Post by por100pre1 on 2007-10-26
> **az said:**
> Not really.  Many problems are solved by dumping your home folder configs (create a new user).

And it's easier to just backup your stuff to external media - safer, too.

Not to mention the issue of running out of space.  If everything is on one partition, you share all the space.  If you keep separate partitions, you run more of a risk of filling one up and having to either move your partitions around (which is not often possible with a full drive) or just starting over from scratch.

I agree with Az completely. With that disk size is more convenient to have just one partition for Ubuntu and swap. The OP could end up needing more space for one of the partitions. Not all configurations are the same. To make backups of the /home folder to removable media or hard disk drive is better protection, specially if the whole disk fails.

---

### Post by mivo on 2007-10-26
> **por100pre1 said:**
> To make backups of the /home folder to removable media or hard disk drive is better protection, specially if the whole disk fails.

I had to re-install Gutsy twice before I went back to Feisty on this machine, which was the third installation of it. A separate /home partition made this a painless and smooth affair. Sure, I could have backuped the files in /home each time and played them back, but that would have consumed more time.

There are few setups where you would need more than 8-10 GB for /. (i.e. using Gentoo, running a mail server that stores mail in /var, running a lot of commercial Linux games, etc.), and in these cases the user usually knows this in advance. If having or not having 3-5 extra GB on a 250+ GB disk became a problem, I would need another or a bigger disk anyway.

I do agree that with a 32 GB disk the matter is different, so just one partition for everything may be more efficient (if someone has a SSD disk, they also have the budget for an external USB disk for backups ;)). In general, though, I think a separate /home partition is more convenient, especially with today's disk sizes.

---

### Post by por100pre1 on 2007-10-26
> **mivo said:**
> I do agree that with a 32 GB disk the matter is different, so just one partition for everything may be more efficient (if someone has a SSD disk, they also have the budget for an external USB disk for backups ;)). In general, though, I think a separate /home partition is more convenient, especially with today's disk sizes.

Yes, if you have, e.g. 250GB disk space the obvious choice is to make separate partitions. That way you could get the benefits of separate partitions without any risk to be lacking free space on any partition. :)

---

### Post by Niniel on 2007-10-26
Btw, what about creating a separate /Home partition for every user? Good idea, bad idea, just plain stupid? :)

---

### Post by Seq on 2007-10-27
> **Niniel said:**
> Btw, what about creating a separate /Home partition for every user? Good idea, bad idea, just plain stupid? :)

Just silly. If you wish to limit data, implement quotas with a single /home

---

### Post by Niniel on 2007-10-29
Oh, I was strictly curious from a data security point of view, not to limit space for users (I'd only have 2 or 3 anyway). You know, if it's good to have one separate /home partition, maybe to have more is even better... 
Also, would that help to keep data and programs separate? Or can anybody mount everybody's /home partition?

---

### Post by gn2 on 2007-10-29
> **Niniel said:**
> Btw, what about creating a separate /Home partition for every user? Good idea, bad idea, just plain stupid? :)

An excellent idea and it has a thread in the Ubuntu Idea Pool: [http://ubuntuforums.org/showthread.php?p=3608812#post3608812](http://ubuntuforums.org/showthread.php?p=3608812#post3608812)

I wouldn't dream of having / and /home in the same partition, it saves hassle having them separate.
For example when 7.10 wouldn't work on my laptop, I got my 7.04 Alternate CD out and re-installed without any loss of data or settings.

The laptop will not run any Live CD as it has a Cardbus CD-Rom drive.

Also 1gb swap seems a bit much, I've never had any problems with 512mb. 

Here's a how-to for creating a separate /home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Depressed Man on 2007-10-29
I personally would do

1-2GBs of Swap (depending on your laptop's RAM).
Some for Home
Some for Music (if your like me and will mess around alot which results in a reinstall so you don't have to keep backing up your music)
rest for /

And Niniel, I think various Linux's OS can mount home. I think some people before Gutsy released were running Feisty with a seperate home and then used gutsy beta which also used the /home.

---

