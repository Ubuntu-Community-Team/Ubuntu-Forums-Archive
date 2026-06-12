---
title: "Install apps on another drive?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by malathion on 2007-11-26
Hi, I recently installed Ubuntu this past week and I've been having lots of fun so far ironing out the kinks. This is my first time using linux. 

I noticed that it seems to have a mind of its own when it comes to where applications should be installed. However, it does not realize that I have a 10gb SCSI drive that I intend to be used exclusively by the operating system, where as I want all my games/apps/etc to be run off a separate, 35gb SCSI. How can I direct Ubuntu to install /usr/Games/ etc to a different path?

Also, I have a few more questions that don't seem to be directly answered in existing threads, but am unsure of the protocol here. Should I post additional questions here or in their own threads? I don't want to spam the forum, if that would be a bother. Thanks for all replies! :cool:

---

### Post by PeterJS on 2007-11-26
There is a method to the madness of where things are installed.
/bin & /sbin are the bare minimum needed to boot a system
/usr/bin is where most programs end up
/etc/ is settings
/usr/local/bin is where things installed specially on that machine go
/usr/lib is where libraries common to a bunch of programs live

and a few other quirky places like /usr/games. Thing is windows isn't like inux, in linux nothing stands alone, hence the need for package management, there is no folder for say the terminal program, it lives in /usr/bin with all the other programs, depends on libraries in /usr/lib, keeps it's settings in /etc/, and probably has files in a few other places as well. While you certainly can move things around given their interdependent relationship of things it's generally not a good idea. Also given that everything you want to run is somewhere on the PATH, there's really no reason to know the exact location of anything as long as it works.

If you want to set up you external partition to be /usr/games, the first thing to do is copy everything in /usr/games to the external disk. Once it is copied over there you're going to want to delete all of the originals. Once /usr/games/ is empty you can mount the other hard drive with all the files there with:
```

sudo mount /dev/something /usr/games

```

Verify that everything ended up in the right place and then we can set it up to automatically mount there on boot.

---

### Post by malathion on 2007-11-26
Ahh I see, that is helpful, thank you!

However, since the other disk is still formatted as NTFS since my migration to Linux, I need to wait until I can back up some of the data on it and convert to the linux filesystem. Another question before I do this: 

I think I understand your proposed solution, and your cautionary warning. :) The problem for me is that 10gb is simply not large enough to include all the games and apps I want to have installed, for example Quake 3, sound/media editing software, Word 2007, in addition to the O/S stuff. So two subquestions:

1) Your solution means I can mount an external drive as /usr/Games/. But suppose I want to have not only /usr/Games/ there but some other parts of the filesystem. Does that horribly complicate things? Or can I mount any individual path as whatever I want? I'll do some googling on the mount command and see if I can't answer this question myself... I had no idea it worked that way.

2) Given that the above might complicate things horribly, would it make more sense to simply format the external SCSI as ext3 and just copy the data from installed games onto it, and run them directly, without trying to move the logical location of any particular filesystem path? Not sure if I'm making myself clear there..

Thanks again!

---

### Post by PeterJS on 2007-11-26
> **malathion said:**
> Ahh I see, that is helpful, thank you!

However, since the other disk is still formatted as NTFS since my migration to Linux, I need to wait until I can back up some of the data on it and convert to the linux filesystem. Another question before I do this: 

Yeah that would tend to throw a wrench in things :)

> 
I think I understand your proposed solution, and your cautionary warning. :) The problem for me is that 10gb is simply not large enough to include all the games and apps I want to have installed, for example Quake 3, sound/media editing software, Word 2007, in addition to the O/S stuff. So two subquestions:

1) Your solution means I can mount an external drive as /usr/Games/. But suppose I want to have not only /usr/Games/ there but some other parts of the filesystem. Does that horribly complicate things?

Horribly complicate is rather subjective, if you're comfortable with partitioning and formatting, it just takes a bit of planning ahead. You can mount one partition in multiple places but I think that would lead to some massive weirdness, if you had two system folders mounted from the same partition. Though not, strictly, required it's generally a good idea to keep a one to one correspondence between mount points and partitions, doubly so if one of those mount points is going to contain system files.

> 
Or can I mount any individual path as whatever I want? I'll do some googling on the mount command and see if I can't answer this question myself... I had no idea it worked that way.

Yeah, isn't it great, you can mount anything you want in any empty directory you want. Which is not to say that every configuration you can think of is useful but what else is new.

You might want to check out /etc/fstab (File System Table), it shows how things are set up to automatically mount, most things in there are mounted at boot unless they have the noauto option, and the only think I think that defaults to that is the cdrom.

> 
2) Given that the above might complicate things horribly, would it make more sense to simply format the external SCSI as ext3 and just copy the data from installed games onto it, and run them directly, without trying to move the logical location of any particular filesystem path? Not sure if I'm making myself clear there..


As in having two copies of everything? one at /usr/games/... and another at /media/someSCSI/...
Yeah I don't think I'm seeing what you're thinking.

---

