---
title: "Ubuntu and NTFS"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by shador on 2006-11-03
So how foes it work really. 

I seem to have no problem using my files on my NTFS partition from ubuntu. though I haven't tried changing anything on that partition from ubuntu yet. What I've heard it isn't too good. 

So, any ideas. Should I leave the NTFS drive as read only?

---

### Post by _lynX on 2006-11-03
> **shador said:**
> So how foes it work really. 

I seem to have no problem using my files on my NTFS partition from ubuntu. though I haven't tried changing anything on that partition from ubuntu yet. What I've heard it isn't too good. 

So, any ideas. Should I leave the NTFS drive as read only?

Without any modifications, Ubuntu can only read from NTFS drives. If you wish to write to the drive, you can use [NTFS-3g](http://ubuntuforums.org/showthread.php?t=217009).

---

### Post by Ecthelion on 2006-11-03
> Without any modifications, Ubuntu can only read from NTFS drives. If you wish to write to the drive, you can use NTFS-3g.

... And risking to lose everything on it ...

Do back up!

Problems don't come immediately, but after some time your disk is messed up

---

### Post by PriceChild on 2006-11-03
Some say it works perfectly...

However, MS have not released the NTFS standards, this mean that all writing to ntfs is purely guesswork.

Backup everything you couldn't bare to live without.

You'll probably be fine, but do you really want to take the chance?

[SIZE=1] P.s. wooo 1 post to go till 2000 :D[/SIZE]

---

### Post by _lynX on 2006-11-03
It's worked perfectly for me for a week of semi-constant use. :)

---

### Post by shador on 2006-11-03
I think I'll keep my NTFS drive read only ^^

Are there other file systems that are supported in both ubuntu and XP that support files larger than 4 GB. That's the main reason for my use of NTFS so far

---

### Post by cotcot on 2006-11-03
Yes Ext2/3. Download in XP the fs-driver from [http://www.fs-driver.org/]("http://www.fs-driver.org/") and install it. Then you can read/write on ext2 or ext3 from XP and linux.

---

### Post by givré on 2006-11-03
> **Ecthelion said:**
> Problems don't come immediately, but after some time your disk is messed up
I'd really like to know how. If there is a problem in the driver that is not known, it should be reported.
Thanks.

PS : If you want to know more about ntfs-3g, the project has a new home page : [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by D10 on 2006-11-03
Both can also read/write fat and fat32.

---

### Post by Ecthelion on 2006-11-04
>  	

[QUOTE]
Problems don't come immediately, but after some time your disk is messed up
I'd really like to know how. If there is a problem in the driver that is not known, it should be reported.
Thanks.

PS : If you want to know more about ntfs-3g, the project has a new home page : [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)[/QUOTE]

I'm afraid I do not have this from personal use...
But while reading the forum I did read posts about people who have had problems...

It's just better to read/write to FAT32.
No problems there, and no need to install any driver.
Writing to NTFS is reverse engineering and well never know if we do it 100% correctly till
> However, MS have not released the NTFS standards, this mean that all writing to ntfs is purely guesswork.

Just warning I'm afraid...

---

### Post by givré on 2006-11-04
Ecthelion, you should know that this is not the only driver/apps made with reverse engineering. Don't forget that even the read part of the ntfs driver is also made with reverse engineering, and everybody know that this just works well. 

They have been working on it since 2001, so you can be sure that it's more than a guess work.

For the post you refer, i'd like to know where and who. This should be due by mistake, and it's could be good to know it. I'm sade to see so much false assumption about ntfs-3g.

You should read the Q&A methods of ntfs-3g : [http://www.ntfs-3g.org/quality.html](http://www.ntfs-3g.org/quality.html)

---

### Post by Ecthelion on 2006-11-04
> Ecthelion, you should know that this is not the only driver/apps made with reverse engineering. Don't forget that even the read part of the ntfs driver is also made with reverse engineering, and everybody know that this just works well.


The thing is... with just reading you can't mess anything up... So there is no risk at all. And that counts.

But you seem to be right... I've done some quick searching to NTFS-writing and I was surprised to find a lot of posts who say it's dangerous and you better don't, but no post about someone actually complaining that their disk did get messed up.

So that leaves 2 options
1. They don't complain because everyone says it's not a good idea to do it and they still did
2. You are right and and NTFS writing is much safer than I expected

And it seems that its rather option 2 than 1.

So I apologize for my preconception,

Ecthelion

---

### Post by givré on 2006-11-04
> **Ecthelion said:**
> The thing is... with just reading you can't mess anything up... So there is no risk at all. And that counts.

But you could read wrong information, not in the good order... things that will not corrupt your drive, but that may crash the kernel, and that's not the case. Read part is much easier than write part, but that should not reduce the performance.

---

### Post by shador on 2006-11-04
Another question, can you convert to ext/3 WITHOUT having to format the disc? I know the program partition magic can convert to FAT32 without wiping everything.

---

### Post by givré on 2006-11-04
> **shador said:**
> Another question, can you convert to ext/3 WITHOUT having to format the disc? I know the program partition magic can convert to FAT32 without wiping everything.
As far has i know, no

---

### Post by shador on 2006-11-04
Well that... sucks =P I have too much to just destroy everything now. But for the nex wipe I'll keep in mind to use EXT3 instead =)

---

