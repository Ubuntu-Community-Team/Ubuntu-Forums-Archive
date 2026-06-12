---
title: "[SOLVED] Filesystem for Arch"
date: 2008-06-30
forum: Arch and derivatives
---

### Post by Inxsible on 2008-06-30
What would be a good file system for Arch?

I currently have it as Ext3, but I have read reports where reiserfs works better and faster. I have also read about differences between reiserfs and ext3 but I couldn't quantify why that would matter to Arch and not to other distros.

Also does it matter if we choose reiserfs or Reiser4 ?

Can someone explain that part to me?

---

### Post by milosz.galazka on 2008-06-30
You need to try them all to find your favorite :)

I am using xfs, but this is just my word.

BTW. It depends on system tasks

---

### Post by Barrucadu on 2008-06-30
ReiserFS is apparently great for /var, due to the number of small files, and increases pacman's performance.

---

### Post by MisfitI38 on 2008-06-30
In Arch, the entire pacman package cache, as well as the ABS tree reside under /var.
XFS is typically a poor choice for /var, since it contains _many_ small files, and XFS is much better suited for large files. 
ReiserFS would be a better choice for the partition containing /var.
[http://bbs.archlinux.org/viewtopic.php?id=51078](http://bbs.archlinux.org/viewtopic.php?id=51078)

---

### Post by Inxsible on 2008-06-30
> **Barrucadu said:**
> ReiserFS is apparently great for /var, due to the number of small files, and increases pacman's performance.

> **MisfitI38 said:**
> In Arch, the entire pacman package cache, as well as the ABS tree reside under /var.
XFS is typically a poor choice for /var, since it contains _many_ small files, and XFS is much better suited for large files. 
ReiserFS would be a better choice for the partition containing /var.
[http://bbs.archlinux.org/viewtopic.php?id=51078](http://bbs.archlinux.org/viewtopic.php?id=51078)
So only for the /var partition, but not the entire root and home right ?

And wouldn't that be true for almost all distros like Debian and Ubuntu as well? 
So why is reiser preferred in the Arch community ?

---

### Post by Barrucadu on 2008-06-30
Arch seems to attract the kind of person that likes to fiddle around with things to get them working as good as possible, and so these things are found. I use ramfs for /var/cache/pacman, /var/lib/pacman, and /var/abs/local. The only downside is that it is risky...

---

### Post by MisfitI38 on 2008-06-30
> **Barrucadu said:**
>  The only downside is that it is risky...
..not with a good UPS. ;)
Invest in a good ups, good hardware and good cooling and you have reduced to your risk quite considerably.

---

### Post by mips on 2008-06-30
> **Inxsible said:**
> So only for the /var partition, but not the entire root and home right ?

So why is reiser preferred in the Arch community ?

Correct.

reiserfs is just the most suitable for /var

/boot ext2
/var reiserfs
/home xfs
/ xfs

Is what I would run if I had my system split up in that manner.

---

### Post by MisfitI38 on 2008-06-30
> **Inxsible said:**
> So only for the /var partition, but not the entire root and home right ?
Either way will work fine. I used Reiser for a year or 2 and it performed well.  
If you have massive directories and files in /home, XFS will begin to become a better choice.
Personally, I use JFS for everything now, it's a great filesystem. One major disadvantage of JFS, though, is that it cannot be shrunk.
All filesystems have advantages and disadvantages.
> 
And wouldn't that be true for almost all distros like Debian and Ubuntu as well? 
So why is reiser preferred in the Arch community ?
The concept that Reiser will perform better with many small files, vs XFS holds true on any distro, yes. However, Arch is unique because it adds a significant number of additional small files to /var, with /var/abs and /var/cache/pacman.
I don't know that Reiser is 'preferred' necessarily, but it will generally perform better for /var under Arch compared to XFS.

ext3 is extremely stable and reliable, and is well supported. It has the disadvantage of being slower to mount, format and fsck. This may or may not be an issue for some compared to others. ext3 can be optimized for performance, and offers 3 modes of journaling. ext3 is slower compared to other filesystems when you really start to push it. 
Reiser is very fast at formatting, but slow at mounting. It is very fast with large amounts of small files, but slower with very large files. Almost a polar opposite of XFS.
JFS is a good compromise between Reiser and XFS in many ways. It offers good all-around performance and uses the least cpu resources. Use it with the deadline scheduler.
XFS is great for servers and for large throughput of large files. If you do a lot of work with large video files, XFS might by something you'd want to check out. Some people swear that XFS works fine for them for everything, but personally I found it much slower with pacman than Reiser.

---

### Post by chucky chuckaluck on 2008-06-30
the first time i installed arch, i used xfs for everything. this time around, i'm using reiserfs for everything. the only differences i notice are in pacman (where using reiser seems to have made it significantly faster) and in opening music folders with cplay (here, using reiser seems to make it take an extra second to open up the folders).

---

### Post by Inxsible on 2008-06-30
Cool. I think going with reiserfs for /var would make sense. What would be an appropriate size for the /var partition ?

I am using ext2 for boot and ext3 for everything else.

---

### Post by Barrucadu on 2008-07-01
Well, my /var is around 300MB, but bear in mind that I clear my pacman cache fairly frequently. If you have space to spare, 1GB would be great. 1GB isn't really that much compared to modern harddrives.

---

### Post by MisfitI38 on 2008-07-01
Why not throw a good 6 gigs at it?
Every single package you install ends up there, and it's good practice to keep your cache rather than clear it.

---

### Post by Barrucadu on 2008-07-01
Why? If I need to downgrade a package I can use ABS.

---

### Post by Inxsible on 2008-07-01
Yeah. I did put in 1 GB of space for var last night. I cannot have 6 GB since I have installed Arch with 2 other distros (well 1 distro with 2 WMs) on a total of 30 GB drive.

Gave 9 Gigs to each distro. Arch is going to be my primary OS on my new laptop-- when I get it over the July 4th weekend :D

Until then...its a triple boot of Debian core + Xfce, Debian core + Fluxbox and Arch + Openbox

---

### Post by MisfitI38 on 2008-07-01
> **Barrucadu said:**
> Why? If I need to downgrade a package I can use ABS.

Of course, that will work.
But the point I was making was that hard disk space is generally cheap and plentiful, and binaries install more expediently. 
After all, we are talking about maximizing performance here, since we are all closet ricers anyway.

---

