---
title: "Dualbooting XP &amp; Ubuntu - some Q's about filesystems"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by GenoSV on 2006-12-19
[SIZE="2"]First of all, sorry for asking a question that has probably been answered several times before, but I used the search and looked through all the thread (ok not all but quite a few anyway), but none did really answer my exact problem, and I wanna be really sure.[/SIZE]

**Summary below!!**
(if you don't wanna read my blablabla crap)

I want to install Ubuntu (or probably Kubuntu but please help anyway :oops: ), but I still need to have XP installed for some of my university work (like inDesign, Photoshop etc that doesn't work through Wine). 
My problem is though that I got two 200GB partions filled with my videos, pics, music etc that I made myself and bought over the years. Those are formatted in **NTFS**.

Using the Live CD for a week it seems Ubuntu has no problem reading these, but it seems as if it cannot write to them.
What I want to do is to keep these partions in NTFS format (since there's no way I can move almost 400GB to someplace else and reformat), but *still be able to write to these partions when running Ubuntu* (which will be "most of the time"). I will use these two to save all my files on.

Also, *which filesystem should I use for my Ubuntu install partion*? Apperently ext3 is default, but when reading around it seems as if it's slowed compared to xfs and reiserFS among others.  

and last (sorry about all the damn questions >_<), *it isn't that hard to dual boot ubuntu with XP is it*? Never did dual booting with linux before so feel a little insecure only. Don't want anything to get deleted or corrupted.

**_Summary_** ^^;;
[LIST]
[*]**Can Ubuntu write to NTFS-partions?** (I have 400GB of ntfs that I wanna use as my working space for my saving files etc)
[*]**What filesystem should I use for Ubuntu?** (is xfs etc really so much faster than ext3?)
[*]**It's not to hard to make dualbooting work right?**
[/LIST]

Thank you so much for all your help in advance. =)

---

### Post by macogw on 2006-12-19
1.  Yes, it can write to them with a bit of configuration crap.  See: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)
2.  I think ext3 is pretty much standard.  No experience to back up the rumours though, sorry.  I can tell ya Reiser murdered his gal so there will probably not be future versions of it as with him going to be spending a long time in the big house... 
3.  It's good to back everything up, but the app Ubuntu uses for install (Ubiquity) is pretty reliable.  Just make sure you run disk defragmentor on your drives about 3 times before attempting.

Moderator's note:  Reiser is still innocent as of now.  He is innocent until he is found guilty at a trial.  He is accused of and so being held on murdering his wife, but so far there is just a preliminary hearing going on.  A preliminary hearing determines whether the accused (Reifers in this case) will face trial or be let go.  There are others working on Reifers file system, so work should continue, though it has been lagging.

---

### Post by Sef on 2006-12-19
> it isn't that hard to dual boot ubuntu with XP is it?

It's not that hard except partitioning can be a pain the first time.  Once you do it a time or two, it is pretty easy.  

Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for installing with the alternate cd.   (A good read still even if you are installing by the Live CD.)

Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing") for installing from the Live CD.

> Also, which filesystem should I use for my Ubuntu install partion?

Ext3 is probably the best.  Reiserfs has not been updated in a while, while xfs is not as stable as ext3 or reifersfs.  Ext3 is the default file system on most Linux distros.

> Using the Live CD for a week it seems Ubuntu has no problem reading these, but it seems as if it cannot write to them.
What I want to do is to keep these partions in NTFS format (since there's no way I can move almost 400GB to someplace else and reformat), but still be able to write to these partions when running Ubuntu (which will be "most of the time").

Linux can read but not write to NTFS.  However, there is some software in beta that can read and write to NTFS.  

> I want to install Ubuntu (or probably Kubuntu but please help anyway  )

Would be better to start off with Ubuntu as more people in this forum are running on Ubuntu and so your questions could more likely be answered.

One last thing before you dual boot:  **BACK UP** you files.   Usually all goes fine, but at times things can get messed up.

---

### Post by GenoSV on 2006-12-19
Thank you for the extremly fast answers both of you :D 

So I guess I should go with ext3 then, I got that cleared up now at least.

As for the ntfs writing part, how good are these beta softwares?
The thread, [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009) , says:
"write support is still a pain (succes in 50% of the case) but because it use fuse, it reside in the user space, and error no more lead to a crash and leat the disk safe."
so it seems as if the hardrive won't be damaged at least. 

About defragmenting, do I need to do that even though I will install ubuntu to a different partion?
Maybe I should clarify what my total hell of harddrive looks like:
HDD1: part1: windows (20GB capacity)
           part2: My music and digicam pics (210gb capacity)
HDD2: part1: *unused partition, planing on putting ubuntu here* (25GB capacity)
           part2: My filmed videofiles and installed games (160GB capacity)

All of those are now ntfs, but I'm thinking about removing the hhd2-part1 (25gb) one, and let ubuntu do whatever it want with that. figured that would be the most secure thing.

Thanks a lot again for the help! 
...and did this Reiser guy really do that? :???:

---

### Post by Sef on 2006-12-19
> About defragmenting, do I need to do that even though I will install ubuntu to a different partion?

It would be best to defrag.   Also you will need a swap partition which should be double your ram.  If you have a gb of ram then one isn't needed too much, unless you do lot of gaming or video editing.

---

### Post by GenoSV on 2006-12-19
> **Sef said:**
> It would be best to defrag.   Also you will need a swap partition which should be double your ram.  If you have a gb of ram then one isn't needed too much, unless you do lot of gaming or video editing.
Ah oki. I'll make sure to defrag all the drives first then. 
I got 2gb of ram, how much swap should I have then? I do some video and editing, although I'll Sonic Foundry Vegas for that so that'll probably be in windows anyway.

And love this community. Thanks for the great helping :D

---

