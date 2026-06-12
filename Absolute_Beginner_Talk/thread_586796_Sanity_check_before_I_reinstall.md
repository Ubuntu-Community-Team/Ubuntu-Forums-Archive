---
title: "Sanity check before I reinstall"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by eyemou on 2007-10-22
As I posted in another thread ([http://ubuntuforums.org/showthread.php?t=581708&page=3&highlight=bsdmainutils](http://ubuntuforums.org/showthread.php?t=581708&page=3&highlight=bsdmainutils)), I've had some issues in my upgrade to Kubuntu 7.10 (I managed to coax it into working, but apt is hung up on one package, that I can neither install/reinstall or remove...). I have a few ideas of things to try when I get home from work, but if all else fails, I may just reinstall.

Before I reinstall, I just wanted to get a sanity check for the following plan to backup my /home/ folder (if in my semi-updated state I cannot run k3b and simply burn what I want/need to DVD):

1. Before backing up my /home/ folder, I have to unmount two large drives which mount at folders in /home/ (/home/me/flac/ and /home/me/flac3/). They've got a lot of data that does not need to be backed up, as they are on separate physical drives.

2. I'm going to re-mount one of the drives, elsewhere (maybe under /media/) outside of /home/.

3. I'm going to simply cp -r /home/* to the newly-re-mounted device.

4. Verify, for sanity's sake, that everything from /home/ copied, including hidden (".") files.

5. Shut down the machine, unplug the extra drives (just to be ultra-safe, as one will be holding my /home/ backup)

6. Reinstall.

7. Once the basic reinstall is finished (with /home/ as a separate partition, this time!!!), I'll shut down, plug in the extra drive, with the backup, mount it somewhere outside of /home/, and copy my entire old /home/ over the clean one.

That would work, right?

Any ideas as to where to temporarily mount the HD outside of /home/? There's no reason as to why i can't mount it anywhere inside of /media/, is there?

As a failsafe, I'm thinking of a Plan B, which is:

tar cvpzf backup.tgz --exclude=/home/me/flac --exclude=/home/me/flac3 /home

This should create a tar archive with the entire contents of my /home/ folder, sans the two large drives, right?

It sounds reasonable... but it would be good for another set of eyes to scan it over, as I've gotten little sleep since messing with the 7.04 > 7.10 upgrade, and it's too easy to get impulsive when you're frustrated.

Thanks!!

---

