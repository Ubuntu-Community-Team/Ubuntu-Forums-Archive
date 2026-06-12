---
title: "So I picked up a WD external HDD today..."
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Griff on 2006-01-06
Set it all up and had no problems.  It mounts automatically and there are no permission issues to deal with.  Here's the problem:

This is supposed to be a 160GB hard drive.  Ubuntu tells me that it is only 149GB.  There are two items already in the drive.  One is autorun.inf and the other is a folder (autorun) that contains wdlogo.ico.  Ubuntu says all this only contains 36KB of data.  Where are the other 10 GB?  And can I delete these items?

Also, the box says it was formated to windows, but it set right up for me with no formatting required.  I would assume it's fat32 except for the fact the box boasts the ability to hold full length DVD movies which would clearly break the fat32 file size limit.  Not that I need to right now, but how would I go about formatting this anyway?  It doesn't show up in gparted.

Thanks,
Griff

---

### Post by curtis on 2006-01-06
Hi,
about you not getting the full capacity...
After file system overhead and actually less space than advertised you end up with a bit less, in your case 10GiB or so.
I'm not sure about formatting it though, you could have a look at cfdisk.

---

### Post by Lambert on 2006-01-06
> The problem here is that there are two different measures of hard
drive storage, both called megabytes.  Computer hardware works on the
basis that one megabyte equals 2^20, or 1048576 bytes.  Hard drive
manufacturers, on the other hand, use a megabyte that has 1000000
bytes, because it makes the drive looks larger.  When buying a hard
drive, you should expect to lose almost 5% of what the manufacturer
claims the drive size to be.

I've read reviews on drives where many people have less. 5% of 160G is 8G, so your ratio loss is a little bit larger then 5%. A review i just read on another WD 320G drive had a loss of 22G so their ratio of actual to claim is about the same as what you're seeing.

there may be some other factor in this.

---

### Post by Griff on 2006-01-06
Excellent.  Thanks for the quick posts.  I'm set now.  ;)

---

### Post by matthew on 2006-01-06
Lambert nailed it. Here's a link to more info: [http://en.wikipedia.org/wiki/Gigabytes](http://en.wikipedia.org/wiki/Gigabytes)

---

### Post by zool2005 on 2006-10-13
> **Griff said:**
> Set it all up and had no problems.  It mounts automatically and there are no permission issues to deal with.  Here's the problem:

This is supposed to be a 160GB hard drive.  Ubuntu tells me that it is only 149GB.  There are two items already in the drive.  One is autorun.inf and the other is a folder (autorun) that contains wdlogo.ico.  Ubuntu says all this only contains 36KB of data.  Where are the other 10 GB?  And can I delete these items?

Also, the box says it was formated to windows, but it set right up for me with no formatting required.  I would assume it's fat32 except for the fact the box boasts the ability to hold full length DVD movies which would clearly break the fat32 file size limit.  Not that I need to right now, but how would I go about formatting this anyway?  It doesn't show up in gparted.

Thanks,
Griff

Hi,

Are you using a "My Book"??

Thanks

---

