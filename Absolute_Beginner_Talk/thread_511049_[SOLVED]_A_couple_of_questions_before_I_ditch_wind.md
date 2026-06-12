---
title: "[SOLVED] A couple of questions before I ditch windows"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-07-27
Before I start I apologise if this rambles a bit - but I would like to get this right first time

I have 2 HDDs - 1 with linux only and completely formatted to ext3, the other has 2 partitions - 1 ext3 the other ntfs with windows. Now that I have an HP printer which I have working through Ubuntu I am in a position to get rid of windows completely.

BUT -  Question 1

I have my music and movies in 3 folders (music split) - 1 is on my /home the other 2 on the ext3 partition of the other drive. I need to get rid of the ntfs partition so I can make the whole partition ext3.

There is just about enough room on the Linux drive to fit the stuff I MAYBE need to move.

Will it be safer and easier to move those files to /home and then use gparted to delete the ntfs, format it to ext3 and make the whole drive 1 partition. 

Or do I need to use gparted to delete both of the partitions on the first HDD and then make 1 new ext3 - then once fstab is sorted I'll be able to move the media files back.

Would moving the files onto /home put me in a situation where I can't boot to ubuntu - or as long as I have spare on / am I ok?

Question 2

At that point I will have lost I believe the boot sector that has the grub (or loader) - so I won't be able to boot to Ubuntu

given that I have to do all this to get rid of the windows partition (At the same time as keeping my files safe :) ) - would it be easier to move the files to /home and just reinstall Ubuntu to my now empty drive and then move stuff about especially as installing it is just sooo much easier than a windows install. Then I would just be needing to get rid of / I assume

The screenshot is of the drives as they are now

TIA

Any thoughts on this will be most gratefully received.

---

### Post by Vaidya on 2007-07-27
Hi.

I quite recently got rid of Win XP :)

I had a dual boot setup and my sound and pix files were on ntfs (legacy of XP).

I felt it safest to back them up on a DVD and just went ahead and partitioned the entire HDD to ext3.

I think it saved me agonising over how to ensure that date was safe on the disk AND made sure that I had a back up of my data which I am a little lazy about backing up.

(please ensure you have cut the DVDs correctly and the data is all there before you do the format!!)

Have fun.

---

### Post by forestpixie on 2007-07-27
Hi - not an option would have to buy a dvd burner - and dvd's and burn 10 of them. 

I'm assuming that if I move the files to the second hdd - they'd be safe there -

---

### Post by Vaidya on 2007-07-27
Well, yes, that does make sense, though I would be really worried about a hard disk failure (maybe not any time now but in the future definitely) AND having all that data lying around not backed up...

Just the thought of losing my carefully built up collection of music and pix made  me paranoid enough to invest into a DVD burner ( and ya, it helps burn those nice movies too... )

Just be careful. I think you should format the other HDD completely, trf data and install the first HDD on Feisty and do try to keep it simple... no fancy options till the system comes back up and you find your data STILL there!

---

### Post by forestpixie on 2007-07-27
> **Vaidya said:**
> ... Just be careful. I think you should format the other HDD completely, trf data and install the first HDD on Feisty and do try to keep it simple... no fancy options till the system comes back up and you find your data STILL there!

I do have it all on disc but they are all on cd's - putting back 60gb of files from cd's is making my head hurt and eyes water :D - 

I had a hdd failure earlier this year so I know that heart in the mouth feeling  - luckily I  had everything on disc - my son however being a teenager thought he knew best :(

Anyway this is more or less where I was thinking of going with this  - at the least the install would know where the old / and /home partitions are.

Do you know if gparted on the live cd can rename the old / and /home partitions so I don't get confused?

---

