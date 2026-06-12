---
title: "replacing hard drive, copying OS to new drive"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by KGH on 2007-08-09
I have two drives, 1 SATA with XP installed, 1 IDE with 2 partitions, hdc1 has Feisty Fawn, hdc2 has Dapper Drake installed. I need the IDE drive for another box and have a new SATA drive ready to take its place. Is their an easy way to copy both OS's to the new drive?

---

### Post by tonyyarusso on 2007-08-23
You may want to read up on either dd or partimage.

---

### Post by crjackson on 2007-08-23
I did exactly the same thing you are talking about.  It did work, but it WAS painfully frustrating.

I used Acronis TrueImage 9.1 Workstation.  I then cloned the old drive to the new drive.

Then I had to edit the grub and fstab files.  I had to uninstall some programs and reinstall them again to get them working.

In the end, it all worked like a champ but if it's possible for you, I would suggest you just back up your /Home folder and any other place that has vital data, then reinstall clean.  Then just copy over the backed up data.

Just my $0.02

---

