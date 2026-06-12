---
title: "external USB HDD permission problems"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by NerdHerd628 on 2007-12-18
OK so here's my problem:

I have a Western Digital 320 GB USB/Firewire/esata external HD and it's giving me woes.  So far as I can tell it mounts fine but when I try to add files to it it denies me with an error message saying that I do not have permission.

Some info about the drive:
I originally partitioned it in Mac OS X into three journaled partitions.  I connect via the firewire cable for my mac laptop and USB 2.0 for the linux machine.

Some info about my computer:
old dell optiplex 240 with 512 mb ram and a P4
using gutsy gibbon ubuntu distro.

any help for a woefully lost beginner?

---

### Post by kesman on 2007-12-19
Have you tried to access the files as root? Try something like gksu nautilus and then locate to the mounted hdd. If this works, then you have to mount the hdd to be available to normal users also.

---

### Post by shadow-of-sin on 2007-12-19
Yeah, copying files over as root should work. What does your fstab file look like? You should be able to change it so you can edit files without sudo by adding the "user" flag in the options "column" in the line for the external drive.

---

