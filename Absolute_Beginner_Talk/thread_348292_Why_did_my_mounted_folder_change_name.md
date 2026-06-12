---
title: "Why did my mounted folder change name?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by davidY on 2007-01-28
Hi, I mounted a partition under /media/documents so that way the folder would always have a link on my desktop. That was all good, but when I resumed my computer today it renamed itself ed on the desktop.... yes on the desktop the folder was called "ed". But the folder is still named /media/documents how can i fix this?

(edited)

---

### Post by Pobega on 2007-01-28
I don't understand your question; Try rewording it, the thing that I don't get is rebanned. What do you mean by it rebanned itself on the desktop?

---

### Post by davidY on 2007-01-28
Oops typo. It renamed itself - the folder now call has as the label: ed

---

### Post by dwblas on 2007-01-28
> but when I resumed my computer today it renamed itself Did you put something in /etc/fstab to mount the directory on boot?  If so, you probably gave it the wrong directory name.  Somewhere, the computer has to have an instruction on where to mount something as nothing will be mounted otherwise so there are 2 possibilities that I can see
[1] The partition is not mounted (a "df" from the command line will tell you).  So what you are seeing is something that was already in the directory "ed" and not the partition you want.
[2] The partition was mounted in a way you don't understand, most likely through an errant entry in /etc/fstab.

---

### Post by corneliusthackery on 2007-03-12
It looks as if I have a similar situation:

I had a windows xp machine, which is now a dual boot with ubuntu (xp on hda1, ubutnu on hda2, hda3 is swap and hda4 is a fat32 which both xp and ubuntu can see and access)

The hda4 was fine for about a week - when this morning I started up and found it renamed as 
"onfiguratio".  I unmounted then remounted, but to no avail.  Its still hda4 - in content - its just that the name is now different.  Checking on XP, everything is fine.

Suggestions?

---

### Post by corneliusthackery on 2007-03-12
Just did a quick re-read of my post - thought I should add one more bit of clarification:

browsing under media - it reads as "hda4" but it shows as "onfiguratio" on the Places selection area, and on the desktop.

---

### Post by jem76msp on 2007-03-19
Same problem here:
Dual boot Edgy - XP, the common FAT32 partition changed name on the Desktop from "storage" to "</html>".
Note that:
1) Where I mount it, in /media, it is still correctly called "storage"
2) In /etc/fstab it is still "/dev/hda5       /media/storage...."
3) In "Device Manager" under "info.product", "volume.label", "volume.policy.desired_mount_point"  is listed as "</html>", while it is listed as "/media/storage" under "volume.mount_point"

It's not a big deal, I can still access and modify all the data, but it smells fishy and it makes me wary...

Alex

---

### Post by corneliusthackery on 2007-03-19
I managed to change the drive name by rebooting into XP, and putting in a new label for the drive - which then showed up as the same name for the mounted drive when I booted back into ubuntu.

It pretty much addresses the visual issue, but it doesn't explain why it happened - but I thought you might find it useful!

---

### Post by jem76msp on 2007-03-30
Yesterday I booted under XP, didn't do anything fancy, and this morning when I booted Ubuntu the correct volume name "storage" was there again...

---

