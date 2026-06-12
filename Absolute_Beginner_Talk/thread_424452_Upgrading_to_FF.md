---
title: "Upgrading to FF"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-04-26
I have edgy eft installed at the moment, running with vista.

when i installed edgy, it picked up my vista partition/bootloader, and was happy to overwrite and add vista into grub.

now, if i were to wipe the partitions where edgy is currently installed, and install feisty fawn over the top, will grub just think, right, i will add feisty, and leave the other two operating systems in place.

i dont really want to reinstall vista, as i had to last time, with no FIXMBR command on the vista disk. is it safe to do what i want to do? or could it end in tears?

oh and by the way, i have never properly got linux going. so i dont care about totally wiping it.

---

### Post by ImpelGD on 2007-04-26
> **SuperAndy said:**
> I have edgy eft installed at the moment, running with vista.

when i installed edgy, it picked up my vista partition/bootloader, and was happy to overwrite and add vista into grub.

now, if i were to wipe the partitions where edgy is currently installed, and install feisty fawn over the top, will grub just think, right, i will add feisty, and leave the other two operating systems in place.

Based on my own, relatively limited, experience of installing Ubuntu with Windows (have done it quite a few times over the past few days) I believe you'll end up with GRUB offering you Windows and Feisty, without an entry for Edgy.

---

### Post by xpod on 2007-04-26
I`ve never had a problem re-installing or adding  any *buntu and a fresh grub has always picked up whatever os`s are there at the time.I did a couple of edgy\fiesty beta installs when i did have Vista on my other drive and it was always picked up ok.

Should`nt be a problem i dont think:)

---

### Post by silverglade00 on 2007-04-26
If you had problems before, it was probably because you have to shrink your Vista partition using Vista, not the tools on the Ubuntu CD because Vista has a new version of NTFS. Since you already have your Linux partitions set, a Feisty install should be almost boring. :)

---

### Post by SuperAndy on 2007-04-26
yea, i shrank my partition in vista, stuck edgy in the gap, it picked it up as vista/longhorn, and life was good.

so, i think i will have a bhas tomorrow.

cheers for putting my mind at rest!

---

### Post by SuperAndy on 2007-04-26
update!

i am posting this from the live boot.

this never worked with dd or ee. so that means the installation should be possible graphically.

Will be a job for tomorrow, i will be sure to post on how it goes. cheer s:D

---

### Post by ImpelGD on 2007-04-27
Good stuff! Hope all goes well.

---

