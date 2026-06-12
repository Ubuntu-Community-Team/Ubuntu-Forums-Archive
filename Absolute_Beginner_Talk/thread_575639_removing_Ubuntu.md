---
title: "removing Ubuntu"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Norm24 on 2007-10-14
I'm still very new to this and need to remove Ubuntu.I some how have managed to screw things up.I actually have it installed twice and both don't work right because I played with settings I shouldn't have.I want to start from the beginning again.

My question is this:after starting Gparted from the Live Cd I don't know what partitions are the Ubuntu partitions.

I too am dual booting with XP SP2.

I'd post a screen shot but don't how with Ubuntu

---

### Post by lemmy999 on 2007-10-14
Go to Applications, Accessories, Take screenshot- its that simple

---

### Post by kshane on 2007-10-14
> **Norm24 said:**
> I'm still very new to this and need to remove Ubuntu.I some how have managed to screw things up.I actually have it installed twice and both don't work right because I played with settings I shouldn't have.I want to start from the beginning again.

My question is this:after starting Gparted from the Live Cd I don't know what partitions are the Ubuntu partitions.

I too am dual booting with XP SP2.

I'd post a screen shot but don't how with Ubuntu

To see what your partitions are, open a terminal and type "**sudo fdisk -l**".  That will list your partitons/drives and the OSs they are formatted for.

Hope that helps.

Kevin

---

### Post by Pumalite on 2007-10-14
Usually Windows is sda1 unless yours is a laptop; then sda1 is small an is the 'recovery partition', Windows is in sda2 and the rest is Ubuntu.

---

