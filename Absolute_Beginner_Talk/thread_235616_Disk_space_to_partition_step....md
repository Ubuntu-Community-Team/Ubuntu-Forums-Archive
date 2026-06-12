---
title: "Disk space to partition step..."
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Jimmyd on 2006-08-13
Well after last night, the cds I got in the mail never worked, they crashed at the install step, all of them, and froze up or went blank. burned a disc from the alternative site an it seems to be working. got to the step "Partition disks" Disk space to partition,  it gives me 3 choices. Erase entire disk:IDE1 master (hda) -6.4 GB Quantum Fireball CX    (2) Erase entire disk and use LVM:IDE1 master (hda)-Quantum   (3) Manually edit partition table.  

so, whats the best choice? thanks in advance, Jim.:-k   oh and if its the last one, what next?

---

### Post by em3raldxiii on 2006-08-13
If you are going to be using your computer for a purely Ubuntu linux install, then going with the default (#1) is the simplest way to go.  Your drive is only 6.4 GB, so I don't think LVM is necessary.  Manually editing your partition table is only advised if you know what you are doing and/or you are attempting to install onto a computer that already has windows installed on it.
 
Some people choose to manually partition their drive and put several partitions specific to their particular user environment.  For example, one fellow I knew put a special partition for the /home directory which would help most if you plan to experiment with other Linux distribitions (so that you don't have to lose all your downloaded stuff and other personal files if you re-install).

---

