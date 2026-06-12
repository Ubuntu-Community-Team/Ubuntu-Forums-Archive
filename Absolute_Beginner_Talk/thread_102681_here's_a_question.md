---
title: "here's a question"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by insub2 on 2005-12-12
with this mount umount stuff, if a hard drive isn't mounted, could one just rip* it out?


*rip: gently  remove

---

### Post by aysiu on 2005-12-12
Yes.
Be sure it is unmounted, though.

---

### Post by earobinson on 2005-12-12
aysiu I want to ask if you are sure, It is always recomended that you power down your computer before doing this no?

---

### Post by aysiu on 2005-12-12
[QUOTE=earobinson]aysiu I want to ask if you are sure, It is always recomended that you power down your computer before doing this no?[/QUOTE] Oh, this is an *internal* hard drive we're talking about?

---

### Post by earobinson on 2005-12-12
[QUOTE=aysiu]Oh, this is an *internal* hard drive we're talking about?[/QUOTE]
rip to me sounds internal other wise it would be unplug but the OP did not say internal or external, I assume internal cuz that is the norm and most people would post external if it was is my guess.

---

### Post by insub2 on 2005-12-12
it is totally internal.
and i am going to power down before removing it.
jsut to be safe.
and i will also have to power down later today already.
so i'll just, you know, take it out when i power down then.
totally.
for sure.

---

### Post by qiemem on 2005-12-12
You should probably unplug your computer too...

---

### Post by red_Marvin on 2005-12-12
SATA is supposed to support hot-swap ([dis]connecting while running) but,
I don't know how linux reacts on it though. ATA I'm afraid, does to my knowledge
not support hot-swap.

---

### Post by doitashimashite on 2005-12-12
** edited out **

---

### Post by earobinson on 2005-12-12
Better safe than sorry :)

---

### Post by SickTwist on 2005-12-12
[QUOTE=insub2]it is totally internal.
and i am going to power down before removing it.
jsut to be safe.
and i will also have to power down later today already.
so i'll just, you know, take it out when i power down then.
totally.
for sure.[/QUOTE]

If you wish to remove a drive while the machine is turned off, Linux automatically umounts *all* partitions before halting so it is not necessary for you to manually unmount them. However, you may wish to edit /etc/fstab to prevent Ubuntu from automatically trying to mount a HDD during the next boot if that HDD has been removed from the machine. Easiest way to do this is to comment out (add a # to the beginning of) any line in fstab that specifies a partition on the HDD you wish to remove. Alternatively, you could add ",noauto" to the end of the options section for any line in fstab that specifies a partition on the HDD you wish to remove. e.g.:

/dev/hdd5     /mnt/backup     reiserfs     defaults,noauto     0     0

fstab lines are made up of 6 columns, each separated by whitespace (doesn't matter how much space). The 4th column consists of mount options which are separated by commas (no spaces) if there are multiple options. The "noauto" option prevents a filesystem from being mounted automatically at boot.

---

