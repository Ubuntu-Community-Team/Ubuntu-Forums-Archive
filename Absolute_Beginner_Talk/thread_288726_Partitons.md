---
title: "Partitons"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by lynxus on 2006-10-30
Hi guys, lil new to teh whole partition thing.

I have a gig or so on teh swap part
i then have 58gb on teh main ext3 part.

how do i go about freeing up lets say 20gb so i can then dual boot the system.

Ive tried in gparted etc but its all greyed out and when i want to unmountteh drive or deactive ate it to shift stuff about it doesnt.


Any ideas?

---

### Post by Kateikyoushi on 2006-10-30
Boot from the live cd and use gparted to repartition the drive.

---

### Post by podunk on 2006-10-30
Back up any important data!

As far as I know you'll have to use a live CD to do this. Once the CD boots you'll be able to use gparted from the command line.

---

### Post by Bartender on 2006-10-30
If you have broadband I'd suggest downloading [GParted]("http://gparted.sourceforge.net/livecd.php") LiveCD.  Follow the links, download it, burn to a CD.  It's the same as the partitioner on your Ubuntu LiveCD, but better.  It has features - such as several text-based partitioners - that the smaller version doesn't have.  I stuck with the graphic interface!  
What's in the main partition now?  If it's Windows, defrag the heck out of it until you're fairly confident the data's been moved as far to the left as it'll go.  Some folks have recommended partitioning while in Safe Mode.  I don't know if that helps or not.
Anyways, the full GParted LiveCD is a handy tool, and I just feel better having it as a separate tool rather than running the Ubuntu CD.

---

