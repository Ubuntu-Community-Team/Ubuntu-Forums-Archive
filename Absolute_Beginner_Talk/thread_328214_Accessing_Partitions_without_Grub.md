---
title: "Accessing Partitions without Grub"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Wight_Rhino on 2006-12-30
This might not be *Absolute* Beginner, but I didn't know where else to put it. Mods can move it if they like.

I have several partitions where I fiddle with distros, (/dev/hdc1, /dev/hdc2...etc) and usually access them with Grub. Recently Arch Paniced on me due to a kernel upgrade, and I would have liked to have gone into /boot to get the new img name to re-enter into menu.lst.

Is there a way to access the file system of a distro on a partition when Grub won't boot it?

---

### Post by 5-HT on 2006-12-30
You can always edit your boot options on the fly from the GRUB screen or just boot into a different distro, mount Arch's /boot and edit menu.lst to your liking. Alternatively, using a live CD to mount /boot and edit menu.lst would work well. 

HTH

---

### Post by Wight_Rhino on 2006-12-30
Ok thanks, just to clarify;

I can mount a partition (/dev/hdc, for example) from a Live CD and view/modify files from there?

---

