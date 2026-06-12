---
title: "No &quot;risize&quot; option in Gparted for Ext3 Partition?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Uncle Spellbinder on 2006-07-16
Hi. I'd like to resize my Ext3 Partition. I don't seem to have a resize option for Ext3 in GParted. It's quite large (123 Gb) and I'd like to reduce the size to around 25 GB and use the unallocated space for other things. Can this be done?

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/UbuntuPartition.png[/IMG]

---

### Post by mostwanted on 2006-07-16
Doesn't that lock indicate that the file system is currently mounted? You can't resize something that is mounted, you'll have to do it from a Live CD.

---

### Post by Uncle Spellbinder on 2006-07-16
Damn!  You are, of course, correct. ](*,)  Sorry 'bout that. 

Would you recommend the Live CD or the GParted CD? Or does it matter?

---

### Post by mostwanted on 2006-07-16
The Ubuntu Live CD (well, desktop CD) has GParted on it if my mind serves me well, well it's integrated into the installer so it must be on there somewhere. That ought to work just as well as the official GParted disc.

---

### Post by Uncle Spellbinder on 2006-07-16
As a friend has my Live CD (trying to create a Linux convert :)), I logged on to XP and downloaded the Official GParted Live CD ISO. Burned it, ran it, worked like a charm. THANKS!

---

