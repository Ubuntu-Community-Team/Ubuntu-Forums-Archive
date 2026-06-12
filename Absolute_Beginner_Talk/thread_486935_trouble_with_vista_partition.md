---
title: "trouble with vista partition"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by amerikkanu on 2007-06-28
Partitioning was never a problem with XP, but having a load of trouble with Vista on a friend's computer.  Gparted says that it cannot resize Vista and recommends that I run chkdsk on it, which I did, which returned no problems (but didn't fix the problem).  I've tried the native vista partition manager, but it says that it can't shrink more than about 6GBs on an 80GB drive, where only 12 GBs are used by vista.  Since it mentions that snapshots and pagefiles could be the problem, I've tried to dig deeper there, but I'm out of my depths there, since I don't like dealing with windoze and don't know too much about it.  Snapshots I don't believe are enabled because I haven't enabled the automatic snapshot/recovery process (though I may be misunderstanding just what the partitioner means by "snapshots" if it doesn't refer to automatic backups).  For pagefiling, I turned it off, set the OS to delete the pagefile at shutdown and then rebooted in safe mode so that my RAM could handle partition resizing.  Still no dice.  Same 6GB shrink problem.

Any linux/M$ gurus have any advice for partitioning in my case?  Also, does anyone know if it's possible to do the following if I can't solve the partitioning problem above:  1.  reformat, 2. partition using gparted, creating a 20GB m$ partition, and 3. install vista from the recovery disks to that partition.  I've heard that windoze will just ignore the partitions on a disk and overwrite the whole thing.  Well, that's easy to check, will google it now.  Any help appreciated!

---

### Post by Seisen on 2007-06-28
Are you trying to dualboot Vista and Ubuntu?

---

### Post by viciouslime on 2007-06-28
> **amerikkanu said:**
> Partitioning was never a problem with XP, but having a load of trouble with Vista on a friend's computer.  Gparted says that it cannot resize Vista and recommends that I run chkdsk on it, which I did, which returned no problems (but didn't fix the problem).  I've tried the native vista partition manager, but it says that it can't shrink more than about 6GBs on an 80GB drive, where only 12 GBs are used by vista.  Since it mentions that snapshots and pagefiles could be the problem, I've tried to dig deeper there, but I'm out of my depths there, since I don't like dealing with windoze and don't know too much about it.  Snapshots I don't believe are enabled because I haven't enabled the automatic snapshot/recovery process (though I may be misunderstanding just what the partitioner means by "snapshots" if it doesn't refer to automatic backups).  For pagefiling, I turned it off, set the OS to delete the pagefile at shutdown and then rebooted in safe mode so that my RAM could handle partition resizing.  Still no dice.  Same 6GB shrink problem.

Any linux/M$ gurus have any advice for partitioning in my case?  Also, does anyone know if it's possible to do the following if I can't solve the partitioning problem above:  1.  reformat, 2. partition using gparted, creating a 20GB m$ partition, and 3. install vista from the recovery disks to that partition.  I've heard that windoze will just ignore the partitions on a disk and overwrite the whole thing.  Well, that's easy to check, will google it now.  Any help appreciated!

Windows won't just ignore the partitions and overwrite the whole disk, but recovery disks might well do so. Gparted doesn't support vista's version of ntfs yet unfortunately. I think that you will be able to do this using partition magic, unfortunately, that's not free.

---

### Post by amerikkanu on 2007-06-28
@seisen, yes, trying to get ubuntu on a friend's machine who made the mistake of vista...

@viciouslime, thanks for the insight.  i'll keep exploring and let others know the outcome, in case anyone finds they're in the same boat.

the promptness of replies never ceases to amaze!

---

### Post by bigken on 2007-06-28
have you defraged the windows partion do this at least twice

---

### Post by bigken on 2007-06-28
also are you using gparted on the ubuntu live cd or gparted liveCD i would recomend using the later

---

### Post by Seisen on 2007-06-28
This should help

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

if that doesn't work google 

**dualboot vista and ubuntu**

---

### Post by amerikkanu on 2007-06-28
@bigken, thanks for the reply.  yes, i've defragged several times and i'm using the latest gparted livecd.  gparted always worked well when i put linux on machines dual-booting xp, but it sounds like it's not there yet with the new ntfs...

@seisen, thanks for the link.  actually i already tried that method.  it's a little frustrating actually because through googling one finds many similar howtos that walk you through how to use a windoze gui, which is pretty self-explanatory...

my problem is that the gui for shrinking the partition won't work, apparently due to enabled pagefiling or snapshots.  i've been googling and trial-and-erroring for hours, and am now on irc.  all suggestions welcome!

---

### Post by bradmayne on 2007-07-03
hey whats up?  I dual boot vista and ubuntu.  Vista boot pro is a free download.  You can resize your hard drive with that.  Just remember not  to format the new partition.  Leave the free space as is.  Then when you go to install ubuntu you can easily install!!

---

### Post by Thesus on 2007-08-28
Hey, I'm having this exact problem, and since the original query was unresolved, I'll bump the thread.

I've owned a Vista machine for about a month. I decided to install Ubuntu. I burned off the ISO, and went to partition the hard drive, which is 106GB, of which 29.5GB is currently free.

Attempting to use the built-in Vista functionality failed. Attempting to shrink the 106GB into two volumes, one of which could house Ubuntu, Vista informed me I could only utilize 1GB of the 29.5GB free. A warning was posted about "snapshots and pagefiles".

Okay, to google. I learn about using 'diskpart' from the command line, but this doesn't help. Shrink commands are still being rejected by Vista, which believes that my free space doesn't exist.

I check my page file, which is capped at 1.4GB, so that's not what's taking up space. I assume 'snapshots' means 'shadow copy', which I check from the command line: 'vssadmin list shadowstorage'. I find that 1.1GB is allocated, and the maximum is 7.6GB. Even knowing this, I still use Disk Cleanup to remove any system restores lying about.

After this, I defragment, as suggested, but Vista still refuses to acknowledge my free disk space. I have thus addressed all the points made below, and googled extensively, without luck.

Thus, help?

---

