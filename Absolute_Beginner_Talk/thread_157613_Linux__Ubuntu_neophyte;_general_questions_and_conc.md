---
title: "Linux / Ubuntu neophyte; general questions and concerns"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Veri on 2006-04-09
Well, here's the story. Had a ~2-year old Maxtor HD, previously set to dual-boot with FC4, and decided to go to Ubuntu after really liking the LiveCD. Halfway through partitioning, the installer red-screened with some error or another - I forget what it said - but managed to wipe out the drive's partition table nonetheless, making it unbootable, and worse yet, unfixable via fdisk /mbr or fixmbr from the recovery console. I barely managed to use a data recovery program to salvage the rather important info from that drive afterwards (had a backup or two, but THAT drive died a week prior, and I was stupidly lax on creating another backup before doing this).

The drive fails Maxtor's Powermax diag tool, throwing "dead6a79" as an error. That util is actually one of only a few things that is even aware that the drive exists.

And so forth. Anyway, that has me a bit concerned as far as initial install, but assuming I get a good backup or two of info and do this again on what is presumably a drive that won't error out on partitioning(!), well...

I am a Linux newbie, and the only reason I want to use it is for sheer personal / intellectual curiosity. I've already read the stickies here, and while I'm quite fluent in most aspects of WinXP, I hate the fact that I'm next to clueless in Penguinese. Short of gaming (DoD:S + Steam, which I don't know how well would run under Cedega/Wine), everything I do on win32 is perfectly doable in *nix.

So basically, I'm just looking for some words of wisdom considering my install "issue" originally was just a fluke on a dying HD (I previously had no problems using a Debian install, so I'm assuming it was). When you were a beginner, what were some of the most helpful things you did or were told to do? What about any epiphanies or anything of the sort?

I'd love to be as comfortable at terminal as I am with XP, but it seems like *such* an extremely daunting task with no apparent beginning point, really. :)

(For reference: 3500+ on Venice; MSI K8N Neo2-F, 9800 pro 128mb (bleh), Audigy 2 ZS. Twin Maxtor 160gb SATA drives (one of which is described above, the dead/dying one), single WD 80gb PATA for backup, another Maxtor 280gb PATA as primary.)

---

### Post by htinn on 2006-04-09
You may seriously want to think about a low-level format.

[http://maxtor.custhelp.com/cgi-bin/maxtor.cfg/php/enduser/olh_adp.php?p_faqid=2221](http://maxtor.custhelp.com/cgi-bin/maxtor.cfg/php/enduser/olh_adp.php?p_faqid=2221)

Hard drives get bad sectors every now and then, so it's probably unavoidable.

---

### Post by Veri on 2006-04-09
Yeah, I'm going to, and probably RMA the thing afterwards since it's still warrantied. May as well replace the drive just in case.

Anyone have advice on the *nix part of things? :)

---

