---
title: "What do we all do every 6 months when a new ubunto comes out - upgrade/reinstall?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-23
Never having used ubuntu before, (or any version of Linux) I was wondering what the standard practice was:

6 months pass and a new ubuntu arrives.

This is of course, assuming you like to have the latest stuff :)

A: Just run the CD and it will upgrade your old version, keeping all data, 3rd party apps and settings intact.

B: backup your data, format your drive and start again from scratch for the next 6 months.

C: there is no need to upgrade as the system gets all the updates over the net anyway.

---

### Post by Programmerer on 2008-02-23
> **PiggiePaul said:**
> Never having used ubuntu before, (or any version of Linux) I was wondering what the standard practice was:

6 months pass and a new ubuntu arrives.

This is of course, assuming you like to have the latest stuff :)

A: Just run the CD and it will upgrade your old version, keeping all data, 3rd party apps and settings intact.

B: backup your data, format your drive and start again from scratch for the next 6 months.

C: there is no need to upgrade as the system gets all the updates over the net anyway.

A: You can do that, but you have to download the alternate cd.

B: That is also a possibility, but not necessary.

C: You can download a new version from Update Manager, System>Administration>Update Manager. All your saved programs and settings won't be affected(unless they won't work in a new version for some reason). It is possibly to just keep the old version, but it won't be supported unless it is a LTS (Long Time Version) version, like Dapper Drake (Ubuntu 6.06)

The best will be to install from the update manager, but if you have a slow internet connection isn't that recommended.

---

### Post by wolfen69 on 2008-02-23
> B: backup your data, format your drive and start again from scratch for the next 6 months.
a fresh install is always best. upgrading ***can*** cause problems.

---

### Post by bhold on 2008-02-23
Some people prefer to reinstall, others to upgrade. You can review 7.04 -> 7.10 experiences in this thread...
[http://ubuntuforums.org/showthread.php?t=580852](http://ubuntuforums.org/showthread.php?t=580852)

Always backup your system, regardless of which approach you decide on.

I would also recommend you wait a week or two until after the official release date before network upgrade or downloading the iso file - these operations are very slow during peak demand periods. 

Verify the md5sum of the downloaded iso file before burning your install disk, this simple step will save you the grief of trying to install from a bad disk.

---

### Post by Programmerer on 2008-02-23
> **bhold said:**
> 

I would also recommend you wait a week or two until after the official release date before downloading the iso - downloads are very slow during peak demand periods.

Yes, and after one to two weeks are many bugs fixed, so it is also more secure to wait a while.

---

### Post by RedRat on 2008-02-23
> **PiggiePaul said:**
> Never having used ubuntu before, (or any version of Linux) I was wondering what the standard practice was:

6 months pass and a new ubuntu arrives.

This is of course, assuming you like to have the latest stuff :)

A: Just run the CD and it will upgrade your old version, keeping all data, 3rd party apps and settings intact.

B: backup your data, format your drive and start again from scratch for the next 6 months.

C: there is no need to upgrade as the system gets all the updates over the net anyway.

_________________________________________________
Well I must say that I was surprised when my system updated from 7.04 to 7.10 back in October. The Installation went very smoothly and I had no problems. Perhaps next time I will not be so lucky. In any case, back up any important data files (pictures, spreadsheets, etc) before you do back up. I think waiting a few weeks is probably a good idea, at least see what bugs others are reporting.

---

### Post by PiggiePaul on 2008-02-23
Thanks.........

Interesting replies.

I guess it's just that I've spend the past couple of weeks learning a bit and playing a lot (plus some hair tugging) getting everything set up in a way I'm happy with.

And as I've come in mid/late ubuntu cycle, I was worried I was going to have to start all over again.

I'm making notes about settings and progs, just in case :)

---

### Post by steveneddy on 2008-02-23
The folks that have problems are the ones who had to hack a little bit to get their hardware working properly in the first place.

I have no major hardware issues so I update from the Update Manager every time.

I have never had an issue upgrading this way.

I started with 6.06 and have upgraded this way since and now I'm on 7.10.

Always a good habit to backup your data before upgrading.

If you do a total reinstall to upgrade, just copy your /Home folder to a flash drive and copy it back after the upgrade.

---

### Post by Programmerer on 2008-02-23
> **steveneddy said:**
> If you do a total reinstall to upgrade, just copy your /Home folder to a flash drive and copy it back after the upgrade.

Yep, but don't do something stupid as copying from Ubuntu, use the Ubuntu livecd, or [Knoppix]("http://www.knoppix.org/"), or another preferred livecd to overwrite the home folder;)

---

### Post by doorknob60 on 2008-02-23
When Gusty came out, I waited a few days (I had to, the servers were slow as hell) then Upgraded with the update manager. But now that I have 3 computers with Ubuntu 32-bit, I'll probably just use the alternate CD so I don't have to download it separately on each computer, and then just do it with Update Manager on my AMD64 laptop.

---

### Post by fracturedmorals on 2008-02-23
> **wolfen69 said:**
> a fresh install is always best. upgrading ***can*** cause problems.

I hate to admit it, but it's true.....a fresh install eliminated the infamous tracker disk I/O woes for me.

Most problems CAN be solved with a bit of handy commandline, but if you're new to linux, then a backup/fresh install is probably the best route to take.

---

### Post by drs305 on 2008-02-23
If you really want it on Day 1, consider getting the nightly build on Day -1. You will be able to download it relatively quickly and the build will be almost identical to the final release. You can then update it after the final is released. I've done it that way several times but now have the patience to wait a couple of weeks to let the dust settle.

---

### Post by Christopher Robin on 2008-02-23
> **steveneddy said:**
> 

If you do a total reinstall to upgrade, just copy your /Home folder to a flash drive and copy it back after the upgrade.

That won't save all the programs and settings, though, will it? Like my Thunderbird address book and saved e-mail; Bookmarks in Firefox, etc. How do I back up and restore all that stuff?


Thanks

---

### Post by Kilz on 2008-02-23
I recommend inexperienced linux users to wait a week after release unless they need the upgrade to help solve some issue. The reason is that while a new release has been tested sometimes a bug slips through. Inexperienced users may not have the troubleshooting skills needed to easily fix those issues. Then after a week when the new release has been installed a few million times and looks safe a inexperienced user can safely install the new version.

---

### Post by crf on 2008-02-23
> **Christopher Robin said:**
> [Restoring a backed up home directory] won't save all the programs and settings, though, will it? Like my Thunderbird address book and saved e-mail; Bookmarks in Firefox, etc. How do I back up and restore all that stuff?

Yes it will. To a point. All your email, firefox settings and personal program settings are usually in your home directory (in files preceded by a dot). So, after upgrading, restoring a backed up home will work. However, be cautious with certain programs. For example, I had a problem with my .gconf file when I upgraded to hardy heron. So I had to replace it, and then recustomize my desktop.

Also, some programs like firefox 3 will see an old firefox 2 profile when they are first run and offer to update the profile using newer configuration files which are formatted differently. So restoring an older firefox 2 profile from a backup when using firefox 3 may possibly result in some strange things happening.

---

