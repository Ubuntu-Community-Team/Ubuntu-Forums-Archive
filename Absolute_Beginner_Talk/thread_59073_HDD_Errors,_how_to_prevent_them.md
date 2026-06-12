---
title: "HDD Errors, how to prevent them?"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by RastaMahata on 2005-08-22
I just booted up my ubuntu pc, when it told me that the drive had been mounted 30 times already, so it had a check (ext3 partition, default).
It found some errors, and I typed e2fsck /dev/hda1. It asked me several times if I wanted to fix (I answered all the questions with Yes), and then told me which files were broken and If I wanted to fix them also (I answered Yes, too).
It finished, rebooted (ctrl+D, or exit), and then it all went well. I reinstalled through synaptic the packages that were supposed to be wrong (twice, the first time it gave me errors), and now I believe everything is well.
Once in IRC (#ubuntu) I was told to use smart tools or something like that. I researched on google but couldnt find anything in the forums nor any other site.
How could I prevent the disc from "breaking"? I already shut down the system through the menu, reset it correctly, I dont use ctrl+alt+backspace, etc...

Please help me, how can I make my system more secure of crashing my HDD? :(

---

### Post by RastaMahata on 2005-08-22
bump? :(

---

### Post by RastaMahata on 2005-08-22
second bump? :( I hope someone can help me

---

### Post by skoal on 2005-08-22
Rasta, I have long since stopped using ext3 in favor of reiserfs, for some (but not all) of the same problems you have been experiencing.  It just seems more robust to me than ext3.  Outside of that irrelevant observation of mine...

Sometimes specific inodes on particular parts of your drive platters will continually give you problems, and the prune/cleaning will just occur over again in time - rinse, clean, repeat cycle.  At one time (while using ext3) I had physically moved a section of my filesystem onto another part of the disk, using an offset.  I believe you can even do this now with parted, assuming you know where on the disk physical defects occur.  I forgot how I determined that with some tool I used, probably using 'e2fsck -cc' or something similiar.

I remember fiddling around with restoring superblock backups, cleaning inodes, etc and just used another drive in the end.  It more than likely wasn't ext3 related afterall, but just the hard drive itself.  Re-installing said software may be a temporary cure, but if it starts manifesting itself again on other applications in time, then you know the ext3 filesystem used those same inodes again - which relate to minute physical defects on your platters.

\\//_

---

### Post by RastaMahata on 2005-08-22
wait.. Let me see if I got it... is reiserfs better that ext3? Because I already changed the HDD (I used to have a Maxtor 40gb, and changed it gor a 120 Gb Samsung). The Maxtor HDD I used to have gave me, IIRC, 3 errors in less than a month.
I'm planning to format when breezy arrives. Would it be a good idea to switch to reiserfs?

---

### Post by skoal on 2005-08-23
1. Tangible differences between reiserfs and ext3?  I know you practice "safe" shut down procedures already, like myself.  But on occassion even I don't, by accident or by haste.  When reiserfs checks it's journals on subsequent boots, it's definitely much faster than ext3 on that front.  Furthermore, in my experience, while searching (via 'du', 'grep', or the like) on hundreds of files, it's definitely much faster than ext3.  Those are just my observations, and I have no statistics to support my wild claims - and any google'd benchmark I may provide would equally be countered by an ext3 link...

2. It does not surprise me that your 40 gig Maxtor had such problems.  I would even venture a guess at the model number: 6E0x0L0, where x=2,3, or 4 (in your case).  Those particular series used Fluid Dynamic Bearings and were notorious with firmware not recognizing them over time due to rotational flux and specific tolerances used in that recognition.  

3. Since you will probably be reformatting when Breezy comes out, I would: 1) run surface disk tests on your current hard drive, 2) make note of what files in what partitions currently give you inconsistencies (corruption), 3) use reiserfs with Breezy, and 4) change your partitioning scheme (in Breezy) to reflect potential surface defects).  In other words (wrt 4):

old:

/boot - 128 MB
/ - 10 GB
swap - 1 GB
/home - rest

assuming all file system problems occurred on your root partition,

new:

/boot - same
swap - same
/opt - 5 GB
/usr/local - 5 GB
/tmp - 1 GB
/ - 20 GB
/home - rest

or something like that.  Just rotate 'em.  At least you'll be moving your important system related stuff to a new physical part of the disk, away from possibly small physical surface defects, inherit on all drives, even in _new_ ones.  That's why a 47 GB drive will be rated only at (say) 40GB.  Similiary, Intel will cast many 3GHz procs from the same dye - some will be rated at 3, others 2.8, and even more at 2.6 (an exaggeration in real production numbers however), and sold as such.

* All this may be overkill in your case, since your experience may only occur just this one time (and for whatever reason).  There may be other causes to your problem as well, completely software related like user accident with 'dd' or the like.  However, your case reflects a lot like my own past ones.  When file inconsistencies progress from _rare_ to often, imminent hard drive failure is definitely one possibility.

\\//_

---

