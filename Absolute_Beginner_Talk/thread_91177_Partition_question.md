---
title: "Partition question"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Coopa on 2005-11-16
My XP partition is dire need of a format and reinstall and i've got a spare 30gb hdd to fiddle with.

Using ubuntu would i be able to install onto my spare drive (D: ), repartition the XP drive (E: ) but only to use the free space of E: to make a new XP only partition(D: or C:?), keeping all my data (work, music etc.) on the old E: drive?

Once this my windows side is nicely cleared up i'll have the hdd space to be able to play around with linux again.

---

### Post by Kyral on 2005-11-16
Yes to everything except keeping the data....if I am following right. Can you explain it a little differently? (Like step by step. I apologize, I seem to be off tonight)

---

### Post by Coopa on 2005-11-16
Sorry, i didn't really explain it very well.

Two hdds:

E: - 120gb, boots XP Pro, and hold my data, about 60-70gig of that i need to hold onto for uni and such.
D: -30gb - Completely empty.

Whilst installing ubuntu on D:, can i use the partition tool to resize the XP partition, making E: into two separate drives. One that i can then reinstall XP on, and one with my data.

---

### Post by Kyral on 2005-11-16
Then its a yes :D

Fire up GParted (PartitionMagic Clone), and resize. Keep in mind that with two partitions, one is gonna show up as C: (whatever one Windows installed on) and the other is gonna show up as D:(the data one)

I reccommend shrinking down the XP partition as much as possible, formatting the freespace as FAT32, transferring the data there (might be a space issue) after mounting it in Linux, then just installing XP and tell it to use the NTFS partition

---

### Post by kruz on 2005-11-16
im not 100% sure
but in knoppix
i used qtparted(i believe thats the name)
and shrank it and it did work(using fat32, not ntfs)
so i would try partition magic, im pretty sure thats the tool of choice
for undercutting xp data
just MAKE SURE you dont have liek 100 gigs of data on the 120 taken
and try to resize xp to 50 gigs
ull almost certainly loose it all
but ive heard good thigns about partition magic(its an xp tool i do believe)
and yes after you install ubuntu, and you have your hardrives setup to boot the D drive first, you can get grub to make hdb and put it on the boot menu

---

### Post by Kyral on 2005-11-16
Defrag the XP drive too before you begin.

GParted/QtParted are basically frontends to Parted in the style of PartitionMagic

---

### Post by kruz on 2005-11-16
[QUOTE=Kyral]Defrag the XP drive too before you begin.

GParted/QtParted are basically frontends to Parted in the style of PartitionMagic[/QUOTE]


oh my bad, i just know if heard people have bad experience
and yes defrag to get all the files to one place on the HD
not really the begging 
because microsoft installs in the middle of the hd.......
::frown face::
ne wayz hopes this helps

tahxn for the backup kyral
and correcting my mistake lol

---

### Post by Coopa on 2005-11-16
[QUOTE=Kyral]Then its a yes :D

Fire up GParted (PartitionMagic Clone), and resize. Keep in mind that with two partitions, one is gonna show up as C: (whatever one Windows installed on) and the other is gonna show up as D:(the data one)

I reccommend shrinking down the XP partition as much as possible, formatting the freespace as FAT32, transferring the data there (might be a space issue) after mounting it in Linux, then just installing XP and tell it to use the NTFS partition[/QUOTE]

What i was planning was installing ubuntu onto the empty drive. 

Then using whatever tool (Gparted, as you say), resize the freespace in the 120gig so that i can reinstall XP on that small partition and use the D: drive soley for data, no OS left. 

I can't really move around the data much. I have enough CD's and space to back up uni work, documents and my mp3 collection. But i don't have enough to back up approx. 60gig of data. Will resizing the D: drive caught data loss/corruption, if there's a good chance of it i'll do a more thorough backup first.

---

### Post by kruz on 2005-11-16
oh in that case
install ubuntu on drive D
boot up
mkdir /windows
sudo mount /dev/hdb1 /windows
then copy all ur needed files
then u can partition the rest of the drive E and make it a folder
like
/home/usr/space
lol

i think thats what u mean

---

