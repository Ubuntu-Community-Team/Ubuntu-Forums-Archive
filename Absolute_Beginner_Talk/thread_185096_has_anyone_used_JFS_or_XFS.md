---
title: "has anyone used JFS or XFS ?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-05-31
I am about to install ubuntu in the next week as I told you before and I was about to go with the default file system ext3 BUT after I saw thouse tests :
[http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)
I thought to miself - why not to go with the JFS file system ?
in almost every test it's the leader
and I have many big files of about 500-1GB

but I don't know if it's relaible , or how is it with small files ?
is it any good ?

---

### Post by skippy81 on 2006-05-31
I use XFS, seems to be marginally quicker than ext3, but its barely noticable.

The thing about all the benchmark sites you see is they have really gone to extremes to drive out a difference between the filesystems - as a home user I doubt you will see the difference.  

In general;-

ReiserFS = good for really small files - if you were running tons of webservers serving mainly small html pages this would be a good choice.  Also probably good for system boot time, since most of the modules etc that get loaded are small files.

XFS = fast all rounder, particulary suited for larger files.  Commonly used on home theatre pcs where huge movie files are regualry recorded and played.

EX3 = maximum compatability with many systems.  Supposedly very reliable. Not partitcualary fast.  

I don't know much about JFS, but I think XFS is considered to be similar to it but better.

If you decide to install XFS, you will need to use a custom partitoning scheme, as linux cannot boot straight from XFS.  You MUST have a small (around .5 gig) partiton mounted as /boot and formated with EXT3.  You can then use XFS for your root and/or home partitions.  Here is my setup:-

Primary 10gb NTFS partiton windows
Primary 500mb Ext3 partition - mounted as /boot
Extended- 
{
Logical 15gb  XFS partiton - mounted as /
Logical 134gb XFS pattion - mounted as /home
Logical 2gb swap partiton
}

---

### Post by Tarhan on 2006-06-02
[QUOTE=skippy81]If you decide to install XFS, you will need to use a custom partitoning scheme, as linux cannot boot straight from XFS.  You MUST have a small (around .5 gig) partiton mounted as /boot and formated with EXT3.  You can then use XFS for your root and/or home partitions.[/QUOTE]
You are not exactly right. All Linux distributions can boot from XFS. However, only lastest versions of GRUB bootloader can correct install it self (from GUI setup). Problem appears in installing first stage in MBR (main boot sector located here) area of hard drive.

---

### Post by simonn on 2006-06-02
[QUOTE=Tarhan]You are not exactly right.[/QUOTE]

And neither are you exactly right :).

See my posts on [http://ubuntuforums.org/showthread.php?t=186715](http://ubuntuforums.org/showthread.php?t=186715)

---

### Post by ththot on 2006-07-06
[QUOTE=skippy81]
If you decide to install XFS, you will need to use a custom partitoning scheme, as linux cannot boot straight from XFS.  You MUST have a small (around .5 gig) partiton mounted as /boot and formated with EXT3.  You can then use XFS for your root and/or home partitions.  Here is my setup:-

Primary 10gb NTFS partiton windows
Primary 500mb Ext3 partition - mounted as /boot
Extended- 
{
Logical 15gb  XFS partiton - mounted as /
Logical 134gb XFS pattion - mounted as /home
Logical 2gb swap partiton
}[/QUOTE]

 I do not know were you take this (wrong) information.

 I have been running Mandriva with XFS on root partititon without a boot partition since years.

 What it really happens is that kubuntu dapper has a bug, what makes that any instalation with XFS as root filesystem fails.

---

### Post by atoponce on 2006-07-06
I've played with JFS, and I wasn't particularly impressed, mainly due to compatibility issues.  If I were you, I would stick with ext3.  It's journaled, still very fast, and universal.

---

### Post by tallman9 on 2007-05-08
I use jfs
/boot ext2
/ jfs
/data jfs

Happy as an elephant, boots fast and uses the least amount of my cpu's power.
> I don't know much about JFS, but I think XFS is considered to be similar to it but better.
They were developed by different companies. And I don't see why one is to be considered better then the other. Everything depends from situation to situation. The one is better at something while the other at something else.

---

### Post by starfry on 2007-06-07
Hi, can someone tell me how to use JFS on Feisty please?

I have tried to "sudo mkfs.jfs /dev/hdb4" but I get " mkfs.jfs: command not found"

I presume I need to install something but I can't find out what....

Thanks!

---

### Post by christhemonkey on 2007-06-07
```
sudo apt-get install jfsutils 
```

Enjoy!

---

### Post by kerry_s on 2007-06-07
i used jfs before, but have gone back to ext2. i wanted to be able to use dsl as my recovery disk and it only supports ext3 and ext2. i find ext2 alot faster than ext3. with ext2 i found it a lot more easier to recover screwed up partions/files.

---

### Post by starfry on 2007-06-10
Thanks christhemonkey! I now have a 175Gb test partition formatted for JFS.

I thought I'd copy my DVDs over to it (via rsync) but it is taking literally hours. Is this normal, it seems incredibly show. Is this normal ? I'm use rsync all the time to copy large amounts of media data around and this is the first time it's still been running the morning after I started.

Both machines are on the same LAN and both are running Linux (not that that should matter)... The JFS partition is on an IDE drive.

Is there something slow about JFS?

---

