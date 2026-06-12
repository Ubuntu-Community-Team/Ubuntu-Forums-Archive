---
title: "Ubuntu 12.04 on MacBook Pro 4,1 freezes during first boot"
date: 2013-06-05
forum: Apple Hardware Users
---

### Post by v1nsai on 2013-06-05
I'm trying to run Ubuntu 12.04 on my MacBook Pro 4,1 with an nvidia geforce 8600.  I used the alternate installer to install it because I was getting a blank screen, but the installed version is also having problems.  When booting without 'quiet' and 'splash', the output just seems to hang at a random spot and nothing ever happens. I used to be able to get to a command prompt by using 'nomodeset', but now I have to use safe mode to get a root shell.  At least I can get that!  I've tried 'startx' and 'start lightdm' but startx output basically says that it can't find a display, and starting lightdm just leads to a blank terminal with a blinking cursor that never does anything.  This makes me think I'm having display problems, but 'jockey-text -l' reports that the nvidia-current driver is enabled but not in use.  Shrug.

I can't access the ext4 partition from OSX, which hasn't played well with Linux at all so far, but I was able to mount my HFS partition and copy over my /var/log folder.  I'm posting boot.log, but I haven't seen anything in there that looks weird.

```
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
/dev/sda3: clean, 176603/305216 files, 859333/1220608 blocks
/dev/sda6: clean, 20/588672 files, 74903/2351872 blocks
/dev/sda1: 8 files, 38554/403266 clusters
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting mDNS/DNS-SD daemon[174G[ OK ]
 * Starting network connection manager[174G[ OK ]
 * Starting bluetooth daemon[174G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [180G 
[174G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned
 * Stopping cold plug devices[174G[ OK ]
 * Stopping System V initialisation compatibility[174G[ OK ]
 * Starting System V runlevel compatibility[174G[ OK ]
 * Starting crash report submission daemon[174G[ OK ]
 * Starting CPU interrupts balancing daemon[174G[ OK ]
 * Starting LightDM Display Manager[174G[ OK ]
 * Starting ACPI daemon[174G[ OK ]
 * Starting anac(h)ronistic cron[174G[ OK ]
 * Starting save kernel messages[174G[ OK ]
 * Stopping log initial device creation[174G[ OK ]
 * Starting configure network device security[174G[ OK ]
 * Starting automatic crash report generation[174G[ OK ]
 * Starting configure virtual network devices[174G[ OK ]
 * Starting regular background program processing daemon[174G[ OK ]
 * Starting deferred execution scheduler[174G[ OK ]
 * Stopping configure virtual network devices[174G[ OK ]
 * Starting save udev log and update rules[174G[ OK ]
 * Stopping save udev log and update rules[174G[ OK ]

```

Could you guys recommend any other log files or suggest something else to try or place to look?  Been at this for a few days now and I'm not even sure that the display is the issue.

---

### Post by este.el.paz on 2013-06-06
Homes:

It seems like you are trying to dual boot Linux and OSX??  Are you using rEFIt or rEFInd?  If not you need to install one of them, rEFInd is newer and perhaps more updated, but it is a boot synchronizer and helps do something (I don't know) so that BIOS??? can recognize the two different systems.  It's been a little while, but you run the install right up until the GRUB install then restart into rEFIt or nd, run the synchronizer, then run back through the install to install GRUB . . . .  I might have used "rodbooks" info on dual booting, which you can find in a search, however I don't recommend using Bootcamp to set up the partitions, it seems to lock the HD and you can't modify it, just use DU.

e.e.p.

---

