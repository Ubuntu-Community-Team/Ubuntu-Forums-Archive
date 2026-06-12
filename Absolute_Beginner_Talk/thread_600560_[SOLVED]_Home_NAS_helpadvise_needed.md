---
title: "[SOLVED] Home NAS help/advise needed"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by nonovo on 2007-11-02
Hi,
I have an older PC at home and would like to utilize as NAS for my other two computers.
The goal is to have disks mirrored and able to spin-down motors to preserve energy and quiet place as well.

Current HW in place.
Dell Optiplex with 1 GHz Pentium and 512 MB RAM
SATA II controller
2x Seagate Barracuda 250 GB Serial ATA II drives
1x PATA connected micro drive 1.0 GB (to be used for OS Ubuntu 7.10)
1x 512 MB flash drive USB as swap  
1x DVD-RW PATA
1x 100MB Ethernet card

I have managed to install OS, with md volume group with 2 mirrored drives (RAID 1) install and configured network with SAMBA server. All seems to work well.
What 'm struggling with is how to send sleep the drives after 15-20 minutes inactivity and wake them up automatically at SAMBA  request.

Does this make any sense (its doable) or shall I forget about it and use it as is?

I was looking at some laptop scripts, but its not 100% what I want, has no RAID (also not sure if the RAID is important bit in sending drives to sleep).

Can you help/advise?

Many thanks,
 Norbert

---

### Post by agurk on 2007-11-02
I'd say it's likely doable. hdparm (IDE) and sdparm (SATA/SCSI) are perhaps the tools you are looking for, they are available in the repos.

---

### Post by nonovo on 2007-11-02
Thanks for the sdparm, would you know how to tie them up? .. or is just enough to set params once, per each of the drive.
N.

---

### Post by agurk on 2007-11-02
Sorry, I am no expert, I haven't even tried these commands myself. But if I should venture a guess, I'd say that you probably need to schedule the command(s) to be run at desired intervals.

Perhaps a useful link: [http://bigblue.res.cmu.edu/mediawiki/index.php/External_Hard_Drives](http://bigblue.res.cmu.edu/mediawiki/index.php/External_Hard_Drives)

Edit: I misunderstood your question. I don't know, but I guess you'd have to issue the command once for each drive in the RAID.

---

