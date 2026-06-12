---
title: "which Version??  probs with 7.10"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by gruss on 2007-12-29
OK I had xubuntu 6.10 working on both an old armada laptop and and old PIII desktop.  Laptop is still fine and I like the idea of a "light" version but I seem to be a little better adapted to my vmware load of ubuntu 7.10..so I tried to install that on the PIII desktop thinking the performance hit wouldnt be all that bad with its 392 meg of ram, plus loaded on a nice fast 200 gig drive should help.  decided to go for it when after an update to xubuntu it crashed hard...figured it was because the silly screensaver kept truning on during the upgrade so threw in the ubuntu text install and kept getting a IRQ11 nobody cares error and it would just stop.  wouldnt really hang, could shut down but wouldnt install?  didnt have this issue loading xubuntu.
So is it ubuntu or is it the version?  Do I need to stick with 6.10 on that machine?  If it makes it to '09 I'd be happy, or would x 7.10 work.
I'm thinking if xubuntu starts to load then so would ubuntu of any flavor but I"m the newb here?  Were the changes really major from 7.04 to 7.10?  would maybe 7.04 work?

All I really want this machine to be able to do is share files, maybe be an occasional FTP server and a pc for the kids to use occasionally.  

Also, if I load the ntfs 3g or whatever on one of the older versions will I be able to share a NTFS folder AND allow write access?

---

### Post by Liolikas on 2007-12-30
> **gruss said:**
> OK I had xubuntu 6.10 working on both an old armada laptop and and old PIII desktop.  Laptop is still fine and I like the idea of a "light" version but I seem to be a little better adapted to my vmware load of ubuntu 7.10..so I tried to install that on the PIII desktop thinking the performance hit wouldnt be all that bad with its 392 meg of ram, plus loaded on a nice fast 200 gig drive should help.  decided to go for it when after an update to xubuntu it crashed hard...figured it was because the silly screensaver kept truning on during the upgrade so threw in the ubuntu text install and kept getting a IRQ11 nobody cares error and it would just stop.  wouldnt really hang, could shut down but wouldnt install?  didnt have this issue loading xubuntu.
So is it ubuntu or is it the version?  Do I need to stick with 6.10 on that machine?  If it makes it to '09 I'd be happy, or would x 7.10 work.
I'm thinking if xubuntu starts to load then so would ubuntu of any flavor but I"m the newb here?  Were the changes really major from 7.04 to 7.10?  would maybe 7.04 work?

There are a lot of changes just look changelog in the site.
And try 7.10 Ubuntu server edition. It gives only command line interface. Then install xorg and fluxbox.
> 
All I really want this machine to be able to do is share files, maybe be an occasional FTP server and a pc for the kids to use occasionally.  

Also, if I load the ntfs 3g or whatever on one of the older versions will I be able to share a NTFS folder AND allow write access?

Yes.

---

### Post by gruss on 2007-12-30
Well what a nightmare ;)  Seems that with my current hardware config 6.06 is what I'm sticking with for that machine, hope I'm not losing out on too much.  Hopefully its more like going from XP back to w2k and not ME!
Loaded 6.06 on a nice big juicy 200 gig drive but then got grub error 18 after letting ubuntu do the partitions so I thought and thought..decided only data would reside on that drive since it will eventually get plucked out and put in a new pc and loaded...I think i finally have a config I can live with and will be semi-future proof IE(wont have to transfer a ton of data when I get a new desktop).
Past installs worked fine on a 20 gig partition for the OS so I'm thinking my current config should work..if anyone thinks otherwise let me know before it finishes ;)
IDE0  w2k3 server loaded on 13 gig drive, no relevance to ubuntu
ide1: 20 gig drive, 8 gig OS ext3, 1.2 gig swap, the rest as fat32 /DOS
ide2: 80gig  NTFS, pictures and important doc backup drive now.  
ide3: 200 gig, data /home only ext2  since I'll be sharing these files with XP machines, I figured if the need came around to move to ext3 the migration is pretty painless?  For now though if it crashed while writing from windows it would have to fsack anyway right?  So any opinions are appreciated!

---

