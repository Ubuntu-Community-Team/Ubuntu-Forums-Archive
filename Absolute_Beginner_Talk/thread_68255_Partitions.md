---
title: "Partitions"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by MuRRe on 2005-09-22
Hi!
I've been reading around now about Linux. Even installed Ubuntu without any major problems.
I have one problem though. Which partitions i MUST have and which i can have and how big these should be.
I have 20 GB to spare for Ubuntu. Please help me sort this out:
/home
/var
/swap
/boot
/user
One more IMPORTANT that i can't remember.
So which do i need, and which can i slope and how big should they be.
People say that /swap should be as big as your RAM. For the other i dont know.
So please do a list for the ones i MUST have (and their recommeded size) and also please an explanation what they do and which format they should have. Like ext2 and ext3.
Just to tell u i have a NTFS (Windows) partion with some music and stuff, can i acces these from Ubuntu??
 ](*,)  ](*,)  ](*,)

---

### Post by Wolki on 2005-09-22
[QUOTE=MuRRe]Hi!
I have one problem though. Which partitions i MUST have and which i can have and how big these should be.
I have 20 GB to spare for Ubuntu. Please help me sort this out:
/home
/var
/swap
/boot
/user
One more IMPORTANT that i can't remember.[/quote]

You need at least two partitions.
/ (containing all the files)
/swap (containing swap memory)

Linux users often recommend having a seperate /home partition. It contains user files and data. Having this on a seperate partition will allow you to reinstall linux (or install another distribution) without losing your data and user settings

How big this partitions are is up to you. I'd recommend 5-10 gb for /, 1/2-1 gb for swap and the rest (i'd say at least 500 mb, more is better) for /home.

You can also create partitions for other directories if you want, but that is only really useful for special configurations, usually not for normal desktop pcs.

You can use ext3 for all of them.


> Just to tell u i have a NTFS (Windows) partion with some music and stuff, can i acces these from Ubuntu??
 ](*,)  ](*,)  ](*,)

You can access, but not write to them. More info here: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

---

### Post by MuRRe on 2005-09-22
Will Ubuntu automaticly use the /home for storing files and settings or do i have to configure this myself.
So
/  -----> 10 Gb ext 3
/swap ------> 1 GB ext3
/home -------> rest

And when i choose for example /swap in Ubuntu installation will it automaticly set all variables correct?
What is with the /user?
Is that if u have multiple accounts or what?
Thanks for your help

---

### Post by Wolki on 2005-09-22
> **MuRRe]Will Ubuntu automaticly use the /home for storing files and settings or do i have to configure this myself.
So
/  -----> 10 Gb ext 3
/swap ------> 1 GB ext3
/home -------> rest[/quote]

During the partitioning step, you can tell ubuntu which partition to use for what. If you do it there (it's menu-based) you won't have to do additional configuration.

> What is with the /user?

It's not /user, it's /usr. It's been backronymed for "Unix System Ressources", it contains program files and data. If you don't do an extra partition for it, it'll be on the / partition, like all other directories that don't have their own partition. This can become quite large if you play around and install many applications and desktop environments said:**
> Is that if u have multiple accounts or what?

No. Multiple accounts are user data, so they are in /home. Each user has its own subdirectory there. For example, my files are in /home/wolki/.

> Thanks for your help

Your welcome. If you have more questions, just ask them.

---

### Post by mlomker on 2005-09-22
> Will Ubuntu automaticly use the /home for storing files and settings or do i have to configure this myself.

If you set it in the installer then the operating system will use them/mount them the way that you select.

The default for swap is 1.5x the amount of memory.  I've heard from people that have regreted going with too small of a swap...if you are over 1 Gig of RAM then it doesn't matter so much.

> 
What is with the /user?


Ubuntu doesn't use /user.  The user directories are under /home.  There is a /usr and that's where certain programs are stored.  I recommend the 3-partition approach...it works well for me.

---

### Post by MuRRe on 2005-09-23
[QUOTE=mlomker]If you set it in the installer then the operating system will use them/mount them the way that you select.

The default for swap is 1.5x the amount of memory.  I've heard from people that have regreted going with too small of a swap...if you are over 1 Gig of RAM then it doesn't matter so much.



Ubuntu doesn't use /user.  The user directories are under /home.  There is a /usr and that's where certain programs are stored.  I recommend the 3-partition approach...it works well for me.[/QUOTE]

So u think i should like i stated before?
This is what i love about the Linux community, "we" can solve our own problem. We dont have to have like 3 million other people with the same problem and then wait for lets say Microsoft to release a fix.
And again, Thanks for your help.

---

### Post by mlomker on 2005-09-23
[QUOTE=MuRRe]So u think i should like i stated before?
[/QUOTE]

Yes, that should work fine.

---

