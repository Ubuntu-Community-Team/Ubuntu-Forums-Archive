---
title: "&quot;invalid file system for this mount point&quot;"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by macogw on 2006-07-18
What does ^ that mean?  It says it while doing (15% of the way through) the /home partition which I set for ext3 (it did that when I set it for fat32 too).  What am I doing wrong?

Here's what I set it for:
it has the fat32 partition with recovery stuff for windows
then ntfs 30gb for /windows
then ext3 5gb for /
then it goes to extended partition and in there are two logical partitions
- 1gb swap
- 69gb ext3 for /home

I also can't figure out how to flag "bootable" for the / partition

---

### Post by catlett on 2006-07-18
I am assuming you are having trouble with the installer. That the installer is sayinmg that ext3 is an invalid file system for that mount point.
Something is amiss because your description of your partitioning is fine.
The only thing I can think of is that the partitions haven't been formatted when you ran the partitioner.
What partitioner did you run? Did you mnakesure to hit apply after partitioning? Alot of partitioners will hold actions until you verify and hit apply.
Which installer are you using? The live cd or the alternate install cd?
If you have the live cd installer. Boot into the live session and enter this command into the terminal (get it by Applications<Accessories<Terminal)
```
sudo fdisk -l
``` This will list your partitions.
You should have 6 partitions listed.
/dev/hda1    NTFS     for windows
/dev/hda2    W95 Fat32    for the recovery partition 
/dev/hda3    ext3    for root
/dev/hda4    Ext (LBA)  for the extended
/dev/hda5    linux-swap  for swap
/dev/hda6    ext3         for home

If this doesn't show 6 partitons similar to this (they could be in different parts of the drive but they will number 6) then they aren't formatted.
Go to System<Administration<Gnome Partition Editor.
This is gparted. You can partition and format from here. Just select your drive and choose "unmount". After it is unmounted you can partition and format. Then try the installer.

---

### Post by macogw on 2006-07-18
the /home one isnt formatted. it says there's used space on it...i'm using the live cd, and right now just going over the whole thing and deleting windows.  i have a reboot disk (very important in my mind) and if my mp3 player doesnt work with linux (my only reason to keep windows) then ill go back over the whole thing with windows and redo the partitioning.  i think i should have defragged before i partitioned.  i thought that since it was a brand new computer it wouldnt need to be defragged.  apparently not.

---

### Post by catlett on 2006-07-18
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) When you finally install, go through the Dapper Guide. It's what I use when settinmg up a new install. 
The guide posts a source list to use. Definately use it and then search synaptic for an appplication for your mp3. One shpould work.
It mau be as easy as installing mp3 codecs.
```
sudo apt-get install mpg321 vorbis-tools
```

---

### Post by macogw on 2006-07-18
yeah there's gotta be something that'll work with it.  its supposedly windows-only...and it's true that macs can't see it, but ive been told that could have to do with a ntfs + mac = no sort of thing.  one of my friends said "get a mac, format the mp3 player, and make it a mac-compatible file-system" i told him i didn't want to lose all my files.  i also don't want to put podzilla on there cuz then it wouldn't be the pretty interface that philips made (which i really really like)

---

