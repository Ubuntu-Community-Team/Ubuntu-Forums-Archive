---
title: "XP + Ubutu --&gt; One Partition..."
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by carpola on 2007-03-18
So it seems I've installed ubuntu onto the one partition I have on my HD (just a low 40 gigs). I want to remove ubuntu 6.06 from my HD so that I can reinstall 6.10 but I fear that (and it will happen) everything will be deleted off my entire HD (windows included).

Is there a way to remove Ubuntu from my XP, even though they are installed on the same HD (no partitions)? Thanks!

---

### Post by gameman12 on 2007-03-18
does xp still work even though u installed ubuntu onto the same partiton?? 

um....i'd repartition the drive so u can use both OSs

---

### Post by carpola on 2007-03-18
Yes, it's dual boot so I can access both of the OS's whenever I want. 

When I was installing Ubuntu, it offered to either reformat my main partition or use the existing space from the main (my 40 gig HD) and put linux onto a new partition. However, I don't see any evidence that there is actually another partition, except for the fact that I can dual boot.

What can I do to remove 6.06 so that I can reinstall 6.10? Will I have to reformat everything and then partition my HD?

---

### Post by gameman12 on 2007-03-18
interesting.....lemme clarify, u can dual boot to both OS's, but there is no evidence of 2 partitions?

you could do it that way, re-partiton enitre disk, but i'm trying to think if there is an easier way....i remeber i tried using gparted to erase an extra partiton and change the size of it but i ended up startin over with a clean install.

can u post the output of

fdisk -l

(l as in LIKE)

---

### Post by Terry of Astoria on 2007-03-18
You must in fact have two or more partitions since Windows and Linux are both running.
You might want to upgrade your existing 6.06 to 6.10. 
You don't have to remove Dapper to install Feisty.

---

### Post by carpola on 2007-03-18
Yes, the only evidence that anything has happened is that 5 gigs off my HD went down. However, this must be the only evidence that those 5 gigs went to the Linux partition. Is there a way to see all my partitions, either from XP or Linux?

I'll go check that command right now.

---

### Post by carpola on 2007-03-18
> **Terry of Astoria said:**
> You must in fact have two or more partitions since Windows and Linux are both running.
You might want to upgrade your existing 6.06 to 6.10. 
You don't have to remove Dapper to install Feisty.

Can you tell me how to update to 6.10? I have the ISO on cd and I've run it LIVE successfully. Thanks!

---

### Post by gameman12 on 2007-03-18
yup, that was the easier way, carpola 	:wink:

---

### Post by carpola on 2007-03-18
haha ok but how do i update it to 6.10? :)

---

### Post by carpola on 2007-03-18
Btw:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        4256    34154190    7  HPFS/NTFS
/dev/hda3            4257        4833     4634752+  83  Linux
/dev/hda4            4834        4863      240975    5  Extended
/dev/hda5            4834        4863      240943+  82  Linux swap / Solaris

```

---

### Post by oilchangeguy on 2007-03-18
read this:
[http://www.ubuntuforums.org/showthread.php?t=386499&highlight=upgrade+dapper](http://www.ubuntuforums.org/showthread.php?t=386499&highlight=upgrade+dapper)
also may i suggest that when you're having a problem, do what i just did to come up with this answer. go to the search box in the upper right of the page and type in what you're looking for. because if you've had problems chances are you are not the first. and a quick search may save you alot of time.

---

### Post by gameman12 on 2007-03-18
ty, see > /dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        4256    34154190    7  HPFS/NTFS


these are ur existing partitions

---

### Post by carpola on 2007-03-18
> **oilchangeguy said:**
> read this:
[http://www.ubuntuforums.org/showthread.php?t=386499&highlight=upgrade+dapper](http://www.ubuntuforums.org/showthread.php?t=386499&highlight=upgrade+dapper)
also may i suggest that when you're having a problem, do what i just did to come up with this answer. go to the search box in the upper right of the page and type in what you're looking for. because if you've had problems chances are you are not the first. and a quick search may save you alot of time.

Thanks, but I'm not new to forums. I did search and read through many pages of threads, yet could not find anything relevant.

---

### Post by H.E. Pennypacker on 2007-03-18
carpola, that means you have more than one partition (five in total, as that command result shows).  As someone else said, just upgrade instead of removing 6.04 to 6.10 (Edgy).  The upgrade instructions are on the Wiki and somewhere on this messageboard.

---

### Post by oilchangeguy on 2007-03-18
try harder. all i did was type upgrade dapper. there are several posts on the subject.

---

### Post by carpola on 2007-03-18
I've seen that link before. The thing is, I don't have an internet connection on 6.06 because my network connection isn't supported. There isn't a method to use the 6.10 desktop cd to update the files, only the "alternate" cd, whatever that means.

---

### Post by Terry of Astoria on 2007-03-18
Well, there are plenty of entries on this forum about how to upgrade. By the way, I meant Edgy Eft, which if I'm not mistaken is 6.10. Feisty Fawn is still unreleased as a stable release.
See 
[https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")

---

### Post by carpola on 2007-03-18
Can I just use the Desktop CD that I burned in the same way that it instructs one to use the Alternate CD?

---

### Post by gameman12 on 2007-03-19
u can't u must either use an alternate cd or just upgrade from the interent. i would recomend the internet because it seems to be less troublesome.

---

### Post by carpola on 2007-03-20
i had to get the alternate cd because my network connection didn't work in 6.06. so i couldn't download it from the internet. i've successfully upgraded to 6.10 now and i have internet access. thanks everyone.

---

