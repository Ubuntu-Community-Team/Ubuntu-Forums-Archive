---
title: "Uninstalling Ubuntu and deleting the entries off of GRUB"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by LandonSmithie on 2006-01-30
Now that I have a dedicated Linux computer upstairs (Vector Linux, it just couldn't handle Ubuntu) I wanted to free up a few (20 >.< ) gigs of space that I rarely use anymore on this comp because they're tied up in Ubuntu. If I get a LiveCD and use cfdisk and clear the linux partitions and swap file how would I go about removing the ubuntu entries from GRUB? (And there wouldn't be any possibility of cfdisk touching my Windows space or corrupting the HD?)

---

### Post by o_fortuna on 2006-01-30
[QUOTE=LandonSmithie]Now that I have a dedicated Linux computer upstairs (Vector Linux, it just couldn't handle Ubuntu) I wanted to free up a few (20 >.< ) gigs of space that I rarely use anymore on this comp because they're tied up in Ubuntu. If I get a LiveCD and use cfdisk and clear the linux partitions and swap file how would I go about removing the ubuntu entries from GRUB? (And there wouldn't be any possibility of cfdisk touching my Windows space or corrupting the HD?)[/QUOTE]
Just edit the GRUB configuration. In a terminal, type
```
sudo update-grub
```
This should get rid of the unnecessary entries. You could also do this:
```
sudo nano /boot/grub/menu.lst
```
Now scroll near the bottom and delete paragraphs that have Ubuntu in them.

---

### Post by LandonSmithie on 2006-01-30
Ok, you forgot to tell me that grub stage 2 miiiiiight be on one of those partitions :P

I'm currently =\ screwed?

---

### Post by morphodone on 2006-01-30
one of the easiest ways to fix your master boot record is to boot from a windows 98 boot disk to a dos console

type: fdisk /mbr

and reboot...into windows only

---

### Post by LandonSmithie on 2006-01-31
I don't have any windows boot disks at all 
I just got out a DSL livecd and I made a 1mb Linux Ext2 partition to save the menu.lst file to


Now what would I have to put in that to boot windows, which is on HDA1 (which is set to bootable)?

---

### Post by LandonSmithie on 2006-01-31
Ok, if I do grub-install... what options would I need to use to get it installed on hda2 and for it to boot hda1?

EDIT: I do grub-install /dev/hda and this pops up:
/dev/cloop does not have any corresponding BIOS drive.

---

### Post by morphodone on 2006-01-31
i still say the easiest way to get rolling is a windows 98 boot disc...

download boot disc [here]("http://www.bootdisk.com/bootdisk.htm")

you can also boot the windows xp cd and run the recovery console and issue the same command (or similar command)

---

### Post by LandonSmithie on 2006-01-31
I got it all figured out, I installed DSL on a fairly small partition and grub is all fixed

(I don't have the windows xp cd, only a restore CD from Sony)

---

### Post by morphodone on 2006-01-31
glad to hear you got it figured out

---

### Post by steve.horsley on 2006-01-31
[QUOTE=LandonSmithie]I got it all figured out, I installed DSL on a fairly small partition and grub is all fixed[/QUOTE]
Excellent.
> 
(I don't have the windows xp cd, only a restore CD from Sony)
<rant>
Do you know, that really pisses me off. They put their own excessive profits above their customers welfare. It has cost me four days from when I wake up to when I go to bed (after midnight) fighting with a so-called restore disk that refuses to do anything of the sort. This, more than anything else, has turned me into a foaming-at-the-mouth Microsoft hater. That they so casually assume I'm going to pirate their software (like you can buy a PC without it!) and deliberately waste my weekends when their software screws up so badly it needs re-installing.
</rant>

---

### Post by Graciosa on 2006-02-16
[QUOTE=morphodone]i still say the easiest way to get rolling is a windows 98 boot disc...

download boot disc [here]("http://www.bootdisk.com/bootdisk.htm")

you can also boot the windows xp cd and run the recovery console and issue the same command (or similar command)[/QUOTE]

Hey,
Could you please explain exactly which CD I need to download? I need to fix the master boot record. After installing Ubuntu , I got "grub ... 1.5 ... please wait... error 21" msg. I only have OEM CD that does not have the recovery console. Managed to source a full XP CD and when I enter the recovery console it will not accept my administrators password.
Any suggestions would be greatly appreciated.

---

