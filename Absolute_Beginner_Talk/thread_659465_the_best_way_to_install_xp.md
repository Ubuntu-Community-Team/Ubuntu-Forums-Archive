---
title: "the best way to install xp"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by snypercore on 2008-01-05
ok heres my question,
as much as ive grown to love ubuntu on my new laptop i think i do need a real installation of XP for games, however i already have ubuntu installed and during the instalation i set it to use entire disk so how can i install XP without messing up ubuntu and grubb?

i just want to shave a few GB's off my main linux partition for XP btw


thanks

---

### Post by metalpancake on 2008-01-05
I don't think you can. you can however install xp over Ubunt and then re-install ubuntu as a dual boot with Ubuntu.

---

### Post by r4ik on 2008-01-05
Please read,

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It is for Vista but should work for XP also if not somebody will correct me.

Good luck !

---

### Post by zvacet on 2008-01-05
Download [Gparted](http://gparted.sourceforge.net/) and resize your hard drive to make space for windows.You can leave it as unallocated space and there you will install windows.After that your MBR will be messed and you will have to reinstall grub.You can try [this](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub).

---

### Post by snypercore on 2008-01-05
the partition manager wont let me resize or edit the partitions in any way

---

### Post by p_quarles on 2008-01-05
> **snypercore said:**
> the partition manager wont let me resize or edit the partitions in any way
Which partition manager? You should use the Gparted live CD that zvacet linked. If *that* doesn't let you resize partitions, please post the output of the following terminal command:
```
sudo fdisk -l
```

---

### Post by snypercore on 2008-01-05
i know this is starting to drift into windows based help but, i used a boot cd to load a partition manager and made 2 new partitions on my hdd, both NTFS and then booted ubuntu and it ran fine with the new parts.
then booted the XP CD and i get an error saying windows did not detect any hard drives connected to my computer? im thinking its either the linux parts or could it be SATA drivers? if it is what can i do about it?

---

### Post by p_quarles on 2008-01-05
> **snypercore said:**
> i know this is starting to drift into windows based help but, i used a boot cd to load a partition manager and made 2 new partitions on my hdd, both NTFS and then booted ubuntu and it ran fine with the new parts.
then booted the XP CD and i get an error saying windows did not detect any hard drives connected to my computer? im thinking its either the linux parts or could it be SATA drivers? if it is what can i do about it?
Yep. Definitely the SATA HD. XP doesn't support them without a hotfix.
[http://articles.techrepublic.com.com/5100-10877-6150784.html](http://articles.techrepublic.com.com/5100-10877-6150784.html)

---

