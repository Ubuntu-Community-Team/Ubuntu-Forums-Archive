---
title: "renaming partitions"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-11
My data partition has previously been in /dev/hda5. I was trying to troubleshoot and I ended up deleting this partition and re-creating it. Unfortunately, it is now /dev/hda10 and yet it remains at the same location. The succeding partition numbers moved down by 1. So what was previously /dev/hda6 is now /dev/hda5, etc.

It looks funny to have my partitions in the following order:
/dev/hda1
/dev/hda10 (data partition)
/dev/hda5
/dev/hda6
/dev/hda7
/dev/hda8
/dev/hda9

How can I rename /dev/hda10 to something like /dev/hda4 to make it look better?

---

### Post by TrendyDark on 2006-03-11
You really can't unless you want to whip out everything and reinstall it all in "pretty" order. The reason that hda4 isn't showing up is probably because it's an extended partition.

Oh, I also noticed your sig, do you need help getting internet working on Breezy?

---

### Post by taurus on 2006-03-11
The first four partitions, /dev/hda1, /dev/hda2, /dev/hda3, & /dev/hda4, are known as primary partitions.  You can only have four primary partitions and if you need more partitions, then you have to created logical partitions from extended partition.  To create logical partitions, you need to use one of the primaries and convert it to extended partition so there is no way you would have /dev/hda4 if you plan to have /dev/hda5 and beyond...

---

### Post by AtinLango on 2006-03-11
[QUOTE=TrendyDark]Oh, I also noticed your sig, do you need help getting internet working on Breezy?[/QUOTE]

Pretty much!

I have a number of earlier threads on my internet problem, but I have been able to sort it to date. let me take you to one of [them]("http://www.ubuntuforums.org/showthread.php?t=139432&highlight=huawei").

---

### Post by AtinLango on 2006-03-11
[QUOTE=taurus]To create logical partitions, you need to use one of the primaries and convert it to extended partition so there is no way you would have /dev/hda4 if you plan to have /dev/hda5 and beyond...[/QUOTE]

/dev/hda10 is the first extended partition. Also, I remember doing this before but not how. It is not so crtitcal a problem, but since this is a learning process, it is good to know.

Thanx.

---

### Post by mackinax on 2006-03-11
> How can I rename /dev/hda10 to something like /dev/hda4 to make it ***look better***?
If only for cosmetic purposes, couldn't you just edit your fstab to mount "/dev/hda10" to "/media/hda4" (or whatever you like), etc.?

Sorry if this was already obvious to you... ;)

---

### Post by AtinLango on 2006-03-11
[QUOTE=mackinax]If only for cosmetic purposes, couldn't you just edit your fstab to mount "/dev/hda10" to "/media/hda4" (or whatever you like), etc.?

Sorry if this was already obvious to you... ;)[/QUOTE]

My /media/directories are already descriptive enough. E.g. /media/Windows, /media/Documents, etc.

However, when I do a *df -h* or when I want to unmount the Documents partition, for example, I am so used to having the Documents mapped to /dev/hda5 (or there around) rather than /dav/hda10. It irritates me, only a bit though.

Even just the way they are ordered. Anyhow, like I said before, it is inconsequential, and may not be worth the effort afterall.

---

### Post by some1_genius on 2007-05-21
alsalamu alikum

here is the thing
--begin
sudo fdisk /dev/hda
p
x
f
w
--end

moustafa

---

### Post by some1_genius on 2007-05-21
don't forget to reboot

---

