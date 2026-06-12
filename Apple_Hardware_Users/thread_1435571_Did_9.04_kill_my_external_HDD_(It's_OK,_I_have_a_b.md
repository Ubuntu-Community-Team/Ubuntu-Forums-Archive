---
title: "Did 9.04 kill my external HDD? (It's OK, I have a backup)"
date: 2010-03-21
forum: Apple Hardware Users
---

### Post by waysaz on 2010-03-21
[LIST]
[*]MacBook Pro 5,1
[*]9.04 Jaunty (from an image made for the MBP)
[*]eSATA expresscard (Startech ECESATA22)
[*]2tb external Fantom drive (Hitachi) attached to above, Mac HFS+ format, 2 partitions
[/LIST]

**Drive will not read on the Mac after booting in Ubuntu!**

I haven't booted Ubuntu in months (October?), but no hardware changes except for the expresscard. Ubuntu runs nicely in a virtual machine from the Mac side, so I made a fresh VM with Karmic. Couldn't remember the cool apps I had running before (it's been a while), so I booted into Ubuntu to check it out. The HDD was connected and on. (Oops.)

It was fine last night on the Mac. I did not notice if it mounted this morning (still in OSX, 10.6.2, Mac sleeping overnight and HDDs on for an unrelated backup). So there is a very slim possibility this has nothing to do with Ubuntu.

Back to Ubuntu, the other external (Firewire 800, HFS+) mounted as usual. Again, I cannot recall if the Fantom mounted. I have not installed drivers for the expresscard/eSATA in Ubuntu (separate driver install is required on the Mac... a rarity). 

I scribbled down the names of the apps I was looking for, and rebooted the Mac to OSX. Where's my HD? Disk Utility sees it as unformatted, and oddly enough, SCSI. If I plug it in via USB, it simply sees an unformatted disk. eSATA is OK with another drive on the Mac.

DiskWarrior failed to see the disk entirely with either connection, same in Leopard and even Tiger.

Could Ubuntu have confused the partition maps or something? Any thoughts on how I might get it running before I give up and restore the backup? Thanks!

---

### Post by waysaz on 2010-03-22
I hate to answer myself, but I was able to repeat the issue.

Reformatted the drive to two partitions on the Mac (GUID partition table, HFS+ format); copied some files to it; rebooted in Ubuntu with HDD on and connected via eSATA expresscard.

Ubuntu sees no drive; gparted sees an unformatted disk if I re-plug via USB.

Mac once again sees an unformatted drive. Guess I'll be very careful when I reboot!

Still, I'd appreciate any thoughts.

---

