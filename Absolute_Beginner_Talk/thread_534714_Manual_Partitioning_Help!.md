---
title: "Manual Partitioning Help!"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Aiello on 2007-08-25
Well, I think something went horribly wrong with my partitioning. I wanted to set up a duel boot with Ubuntu and Windows XP, with Ubuntu only having 13gb or so. 
This is what my partitions table originally looked like: [IMG]http://ubuntuforums.org/attachment.php?attachmentid=41531&d=1187971851[/IMG] 

I then followed these instructions: 
OK, this is what you have to do.

1. Run the Windows defragment utility several times to clean up your partition and make it easier for the installer.

2. Shrink the ntfs partition by right-clicking and selecting re-size. Remove 13Gb (or however much you want to give ubuntu).

3. Create the ubuntu swap partition by right-clicking on the free space, and selecting new partition. Give this partition only 2x your ram amount (1000Mb should be fine if you don't know your ram amount). Put it at the beginning of the free space, and make it of type linux-swap.

4. Now create another partition using all of the remaining free space. Make it ext3, and set the mount point to /.

Your table should now look something like this:
Device Type Mount Point Size
/dev/sda1 fat32 /media/sda1 41 MB
/dev/sda2 ntfs /media/sda2 66000 MB
/dev/sda3 swap 1000 MB
/dev/sda4 ext3 / 13000 MB

I have what my partition table looks like now uploaded.

When I click Forward in the installer I get this warning: File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 20017 (39957 expected); size of FATs is 79 sectors (157 expected).

Fearing I will kill my HDD, I click cancel. I then get this pop up: The test of the file system with type fat16 in partition #1 of SCSI1 (0,0,0) (sda) found uncorrected errors.
If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.

I click go back, and it brings me back to the partitions table.
I need some serious help! I am a complete newb and I think I got myself over my head!
-Help! Thanks!

---

### Post by Aiello on 2007-08-25
Seriously guys. I REALLY need help here. I am afraid to exit the installer because all the damage I did might be come irreversible. I am freaking out right now!:(

---

### Post by Niklas Schröder on 2007-08-25
try this.

```

ALT>>F2

```

```

gksudo gparted

```

if that doesn't work, do...

> 
System>>Administration>>Gparted


post a screenshot of that if it opens.

---

### Post by Aiello on 2007-08-25
Here it is.

---

### Post by Aiello on 2007-08-25
Any idea on what I can do? How much damage did I cause? *begging*

---

### Post by Niklas Schröder on 2007-08-25
hang on a sec.  i just got back from my neighbor's house (dog sitting their she-devil).  let me take a look.

---

### Post by Niklas Schröder on 2007-08-25
ok.  doesn't look like you've done any damage.  here's what i'd recommend.  

take a look at the image i've linked to. 

> 
[http://i159.photobucket.com/albums/t147/clipsandeggs/Gparted.png](http://i159.photobucket.com/albums/t147/clipsandeggs/Gparted.png)


open up gparted again (like i told you how before), click on the large partition, hit "Resize/Move" and drag the right side of it to about where i drew the line.

hit "Apply"

it'll probably ask you if you really want to resize.  hit yes or a similar option.

then go back to the installer (after the partitioning is done) and hit "Install in largest empty contiguous space" (something like that, i don't remember EXACTLY what it says).  it should then install in the unallocated space you just created.

on question before you do that though.  did you defragment your windows partition first through windows?  i don't normally do that with mine, but it sometimes helps keep the errors to a minimum (i don't think you'll have any problems though).  

let me know how it goes.  :)

---

### Post by Aiello on 2007-08-25
Thanks for the reply. Before I go any further I have a question.
This is a family computer, so I want Ubuntu to have only 13gb or so. Can I resize the Windows or Ubuntu partition so Ubuntu only has 13gb?
-Thanks again!

EDIT- Yes, I did defrag Windows.

---

### Post by Niklas Schröder on 2007-08-25
absolutely.  but i would make the ubuntu partition bigger than that to start.  then you can resize it through gparted after you have it successfully installed.  in my experience, nothing with partitions is final, you can ALWAYS go back and change stuff later.  ;)

---

### Post by Aiello on 2007-08-25
Thanks! Well here goes nothing. Oh, and I blame you if something goes wrong.

Just kidding!:lolflag:

---

### Post by Niklas Schröder on 2007-08-25
lol.  if something (by some small chance) did go wrong, you'd have every right to blame me.  but the ubuntu cd works wonders as a rescue disk too!  [IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/chair.gif[/IMG]  lol.  i don't think anything will go wrong though.  i've re-partitioned my machine multiple times with no problems.

---

