---
title: "Mirroring NAS units"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by drsox1899 on 2008-03-15
I'm looking for a very specific backup solution involving 2 RAID NAS units and 1 PC.

I have an Infrant RAID NAS that I use as a BIG remote disc ( 4x750GBs) and as a Music Server for SONOS. I have another Infrant RAID NAS that I use as a backup. Every week I backup one to the other using Retrospect on WinXp to duplicate only what's new/changed.

I want to find a Ubuntu equivalent so I can replace the WinXp with Ubuntu.

I can't load any server oriented S/W on the NASs - they run as closed UNIX boxes. Nor can I use Grsync on the Ubuntu PC as both the source and the destination are Remote. I don't want to back up anything on the PC as I can do this manually.

I have an option to use VirtualBox/VMware on the Ubuntu PC to run a virtual WinXp running Retrospect - but it seems to me a real clumsy way (and possibly unreliable).

I've looked at most of the options listed on these forums but they seem to assume EITHER
1. Some form of server S/W can be installed on the remotes OR
2. The source data is local

Any ideas ?

Regards

---

### Post by herbster on 2008-03-15
You can use rsync if you were to mount the drives, so rsync acts as though the source is local. I have an XP box on my home network whose partitions are mounted and I do backups with rsync nightly.

---

### Post by drsox1899 on 2008-03-16
Thanks, i'll try it.  I can't seem to do the same with Grsync which would be preferable to rsync.

Regards

---

### Post by herbster on 2008-03-16
What do you mean? Grsync = rsync. Have you tried what I advised or are stating that on prior experience(s)? If you need any clarification, shoot! :)

---

### Post by drsox1899 on 2008-04-12
I haven't progressed any further yet as I have spent the last few weeks getting all the bits for a new PC together.  This one is for experimenting with Ubuntu.  

It now has been built and I'm installing 8.04 to get over some VirtualBox USB problems woth 7.10.

rsync is next on the list.

Thanx

---

