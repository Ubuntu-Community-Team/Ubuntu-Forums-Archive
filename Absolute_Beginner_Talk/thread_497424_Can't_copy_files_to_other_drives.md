---
title: "Can't copy files to other drives?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-10
Hi. 

LOL. This is kind of embarrassing, but i just realized that i can't copy files to my other drives on my PC, it says that i do not have permission to these drives. What to do? It's probably just a simple thing.

---

### Post by hyper_ch on 2007-07-10
well, you need to have write rights for that user on those drives.

Where do you try to copy them to?

---

### Post by alienexplorers on 2007-07-10
you have to use chown to make the partition/drives readable by you.

---

### Post by czepluch on 2007-07-10
> **alienexplorers said:**
> you have to use chown to make the partition/drives readable by you.

I can see pictures and play movies and stuff like that from the drive, and i can copy things from the drives to my linux drive, but not from my linux drive to those drives. It's the other drives on my PC.

---

### Post by czepluch on 2007-07-10
What do i do ? Anyone?

---

### Post by alienexplorers on 2007-07-10
When you check the drive permissions in Nautilus what does it show as owner.

---

### Post by czepluch on 2007-07-10
> **alienexplorers said:**
> When you check the drive permissions in Nautilus what does it show as owner.

its says that root is the owner

---

### Post by alienexplorers on 2007-07-10
Try using > sudo chown yourname:yourname *

---

### Post by hyper_ch on 2007-07-10
don't forget the sudo :)

---

### Post by zoogTHOMzoog on 2007-07-10
If the other drives are NTFS (Windows) then you need NTFS support to write to those drives... there are many howto's on this forum, try [this one]("http://ubuntuforums.org/showthread.php?t=217009&highlight=howto%3A+ntfs+write") .

Cheers.

---

### Post by czepluch on 2007-07-10
> **hyper_ch said:**
> don't forget the sudo :)

I've tried but still no change ?

What do you mean by remember the sudo? Is it because there is an other sudo than the normal when i'll have to acces another drive ? The drive i want to acces is: sda5

---

### Post by doomster on 2007-07-10
if you used your other drives in windows, probably they are ntfs formated. to enable -write support to ntfs drives you will have to use ntfs3g program... Installation instructions are [here]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

---

