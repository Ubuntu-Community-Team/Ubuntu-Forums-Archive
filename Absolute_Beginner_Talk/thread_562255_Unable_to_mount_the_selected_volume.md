---
title: "Unable to mount the selected volume ?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by veryforeign on 2007-09-28
First of all, hello - i'm a very new Linux and Ubuntu user 

Secondly, i did search through the other similar threads about this problem, but as I'm new to this, I'd really want someone to take a look at my specific problem as i'm not really able to understand the concepts and apply them myself, if you know what i mean. 

So, I have 1 hdd, a 120 GB SATA on my notebook. It came with Windows Vista pre-installed on a hidden partition. i quickly ditched it tho, and installed XP instead and Ubuntu. So now I have a 10 GB hidden partition with Vista packed, antother 10 GB partition with Ubuntu, and 2 more partitions of 40 and 50 GB (one with XP, the other empty). The filesystems on the 3 usable partitions is NTFS.

Now, in Ubuntu, I can't access any of the 40 or 50 GB partitions (only the linux one). I get this error message:

"Unable to mount the selected volume" - Details: error: device /dev/sda2 is not removable / error: could not execute pmount"

So, what i want is to access sda2 and sda3. optical drive works btw. just tell me what info i have to provide you guys with, and what to do. As I said, Linux newbie so... be gentle :)

Thanks!

---

### Post by dje on 2007-09-28
Try this:
[http://www.arsgeek.com/?p=585]("http://www.arsgeek.com/?p=585")
Hope that helps :)

---

### Post by veryforeign on 2007-09-28
I've tried installing programs from both articles, but none can be found

tried sudo apt-get install libfuse2 fuse-utils libntfs8 ntfsprogs and also sudo apt-get install ntfs-3g . seems they're not available anymore.

so i'm back to square one. how can i use my ntfs partitions :-<

---

### Post by dje on 2007-09-28
What version of ubuntu are you using?
try here:
[http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")
hth

---

### Post by veryforeign on 2007-09-29
Thanks mate, solved through that link!

---

