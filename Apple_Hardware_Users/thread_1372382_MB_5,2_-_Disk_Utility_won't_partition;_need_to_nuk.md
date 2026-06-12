---
title: "MB 5,2 - Disk Utility won't partition; need to nuke and pave; have questions"
date: 2010-01-04
forum: Apple Hardware Users
---

### Post by mailman1175 on 2010-01-04
Hey, all,

I've been toying with linux for about a year and a half, and just got a new 13" MacBook in July. I'd like to carve out a partition for Karmic on the MacBook, but neither Disk Utility nor Boot Camp will allow me to do so. Both utilities say something about needing to format the drive and reinstall.

My Time Machine backups are up to date (as of just a few minutes ago, as a matter of fact), but I've never restored from Time Machine. I understand that I need to boot with the Snow Leopard disk I have, and that I'm to choose "Restore from backup" (or something to that effect, anyway).

What I don't know is if I'll get the opportunity to reformat/repartition the drive at that time, or if I should boot to the system disk, reformat, repartition, THEN restore from backup.

With our cheapo little netbook I don't mind plowing in and figuring it out as I go. The MacBook's a different story. I'd just like to have an idea of what I'm getting into before I get there.

TIA

---

### Post by mailman1175 on 2010-01-04
As far as that goes, since I'm formatting/repartitioning (for a dual-boot, OS X and Karmic-Gnome), I might as well go ahead and set up a few different partitions, for /Users (OS X) and /home (linux), because I'd like to be able to at least access each operating system's data from the other.

I've found a [few]("http://www.macosxhints.com/article.php?story=20040716153639236") [things]("http://www.insanelymac.com/forum/lofiversion/index.php/t144411.html") about partitioned OS X installs, and the current Ubuntu installs I have going have /home on a separate partition.

This presents a question (or two or three)...
[LIST=1]
[*]What do I need to do in order to symlink, say, /home/jeff/Documents, et al, to their respective OS X counterparts? I gather the "shared" partition will need to be a non-journaled HFS file format. I assume (from previous experience) that usernames and passwords will need to be the same on both platforms. What else?
[*]Assuming I'm symlinking the /home/* directories to /Users/* directories (rather than the other way around), what's the bare minimum size partition I could get away with? 512MB? The reason I ask is because I obviously don't want a bunch of unused capacity hanging out in partitions I can't usefully access from both systems. The HDD is 500GB, and it's already about half full, just with OS X.

I can probably shrink the installed size of my OS X install some (by moving things off onto an external drive), but until I can get a NAS device set up here, I'll have to live with what I've got.
[/LIST]

So, anyway, I'd love to hear from you folks who've been dual-booting: How are you partitioned, and if you were in my shoes (starting both installs from scratch), would you partition differently than you already are?

Again, thanks! [If y'all think I'd be better served to roll this second post out into a separate thread, by all means, let me know... I just thought the two were closely-related enough to justify being in the same location.]

---

