---
title: "automatically mounting new hard drives in kubuntu 7.10"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by malathion on 2008-03-08
I work in a computer repair shop and we have a kubuntu gusty box in here for data recovery. We occasionally hook up customer's hard drives to copy data to the file server. I dont want to have to explain to anyone how to mount a hard drive and would prefer if every device got automatically mounted at startup and shortcuts on the desktop, something like the behavior of the Knoppix LiveCD. Is it possible to do this with kubuntu? 

Just to make clear, I am not having any problem with fstab and all my local drives are mounting perfectly-- its only whenever I hook up a NEW device that I want this behavior. 

Thanks.

---

### Post by herbster on 2008-03-08
A new internal or external device?

---

### Post by malathion on 2008-03-08
> **herbster said:**
> A new internal or external device?

Thanks, all new devices will be connected internally.

---

### Post by malathion on 2008-03-08
bump

---

### Post by herbster on 2008-03-08
AFAIK, you can't just plop a new internal drive and have it mount perfectly without editing your fstab, and doing so also depends on the filesystem.

---

### Post by malathion on 2008-03-08
> **herbster said:**
> AFAIK, you can't just plop a new internal drive and have it mount perfectly without editing your fstab, and doing so also depends on the filesystem.

As a linux n00b this is a bit hard for me to accept considering that the knoppix livecd already has this functionality... are you sure that this is not possible? Anyone?

---

### Post by Inxsible on 2008-03-08
you can use pmount to mount the drives. This will force your drives to be mounted under /media.

pmount is usually used for external drives, but it should work for internal drives as well

---

### Post by ODF on 2008-03-08
since you're using kde I dont know exactly but in gnome gparted is really nice.

Can you run it in kde ? I hope =)

---

### Post by malathion on 2008-03-08
> **Inxsible said:**
> you can use pmount to mount the drives. This will force your drives to be mounted under /media.

pmount is usually used for external drives, but it should work for internal drives as well

This sounds interesting... can I run this automatically on startup so it will mount everything? As I said above, my main issue is that the other people in the office have no interest/time to learn linux command line, so I need this to be idiot proof. I'll try it when I go in tomorrow, but anythnig else you could add would be great in the mean time... thanks

---

### Post by phelixnyc on 2008-03-08
In Ubuntu using gnome you can just add/remove ntfs3g app. Try this in Kubuntu.

---

### Post by herbster on 2008-03-08
If you're using HAL, it will automount, that's how Knoppix works from what I recall. If you're using an ntfs drive you'd probably need ntfs-3g as noted above.

---

### Post by malathion on 2008-03-09
```
pcmax@pcmax-desktop:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

As I understand it ntfs3g is just for reading disks, what I need is to AUTOMATICALLY MOUNT THEM at startup...! not just be able to mount them through command line.. I think Ive not been sufficiently clear about what I am trying to do... I'll try this HAL thing though, is there somewhere I can read more about it? Thanks

---

### Post by herbster on 2008-03-09
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

You may want to try that.

Also, to mount ntfs drives with the ntfs-3g GUI, this will do it in a jippy: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by ghost_ryder35 on 2008-03-09
you could also get an external enclosure for a 3.5" drive and mount it that way, then it would automount since it is USB :)  then again it would be a tad slower....

---

