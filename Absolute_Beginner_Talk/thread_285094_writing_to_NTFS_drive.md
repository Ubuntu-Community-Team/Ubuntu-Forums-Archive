---
title: "writing to NTFS drive"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-10-26
I have kubuntu 6.06
how do I write to ntfs drives??
Is it safe to do so from linux??

also
how do I read/write to linux partition from winxp??

---

### Post by Ecthelion on 2006-10-26
These are usefull links for reading/writing from linux on ntfs/fat:

[http://ubuntuguide.org/wiki/Dapper#H...read.2 Fwrite]("http://ubuntuguide.org/wiki/Dapper#H...read.2 Fwrite")
[http://ubuntuguide.org/wiki/Dapper#H...o_read.2Fwrite]("http://ubuntuguide.org/wiki/Dapper#H...o_read.2Fwrite")

---

### Post by PriceChild on 2006-10-26
Writing to ntfs is not reccomended.

[COLOR=Red]**Y****ou may experience HUGE DATA LOSS**[/COLOR]. Do NOT use on production machines and backup all data.

You have been warned.

---

### Post by Ecthelion on 2006-10-26
> Is it safe to do so from linux??


It is safe to read/write on fat32
It is also safe to read NTFS.
They say it is not entirely safe to write to NTFS, but they say that to make sure they couldn't be hold responsible if any problem would happen

It as safe as they could get it.

EDIT:

> Writing to ntfs is not reccomended.

You may experience HUGE DATA LOSS. Do NOT use on production machines and backup all data.

You have been warned.

I'm absolutely not a pro but isn't that exagerated?
They make no problem to resize etc...

---

### Post by compmodder26 on 2006-10-26
No actually I have first hand experience on how destructive it can be.  I crippled my Windows installation by trying it.  Granted that was over a year ago, but I did lose massive amounts of data.

---

### Post by PriceChild on 2006-10-26
Many people report it works fine... but then there are those who have there entire partion wiped.

There are guides in the faqs, howtos tricks and tips forum, they also have warnings above them.

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs)

---

### Post by givré on 2006-10-26
> **PriceChild said:**
> there are those who have there entire partion wiped

Simply wrong.

---

### Post by PriceChild on 2006-10-26
> **givré said:**
> Simply wrong.Not many... but i have heard of it!

---

### Post by bulldog on 2006-10-26
> **givré said:**
> Simply wrong.

Could be,but I did it on a Fedora4 install some time ago and it messed up my partition.

It started fine but after a few months I had to do a reinstall.
Not lost any data but a warning is in place.

It wil not break your NTFS partition right away,but you should be aware it can happen.

---

### Post by jhenager on 2006-10-26
I have Ubuntu on hda1 and hda5.
I have Vista on hdb.

It was fairly easy on my SuSE system to see my Windows files. I just want to connect to Vista to grab some wallpapers, copy bookmarks, etc.

Don't care to write to hdb.

---

### Post by bulldog on 2006-10-26
> **jhenager said:**
> I have Ubuntu on hda1 and hda5.
I have Vista on hdb.

It was fairly easy on my SuSE system to see my Windows files. I just want to connect to Vista to grab some wallpapers, copy bookmarks, etc.

Don't care to write to hdb.

Just mount the partition you want an you can copy as much as you want.

```
sudo mkdir /mnt/vista
```
To make a mount point.

```
sudo mount -t ntfs /dev/hdb /mnt/vista
```
To mount your Vista.

---

