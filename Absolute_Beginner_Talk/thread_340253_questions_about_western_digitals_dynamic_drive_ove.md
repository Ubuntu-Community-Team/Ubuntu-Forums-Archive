---
title: "questions about western digitals dynamic drive overlay"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Huntz23 on 2007-01-16
I am running a dell 4400 with a maxtor 20gb hd and a western digital 80gb hd.
I was setting up a dual boot system with xp on the 80gb and Kubuntu edgy on the 20gb hd, and installed grub in what I believed to be the MBR.  When I restarted it come up 'Error loading OS'.  I just figured that Grub had a hiccup and minced the mbr a bit(wouldnt be the first time its done it to me.)  I put in my xp disk and loaded up the recovery console and fixmbr did nothing.  So I used the western digital disk that came with the drive to see it MBR tools would would and the disks partitions had been wiped clean( it was setup for two 40gb partitions).  

The last time I formatted the disk it used Ontrack DDO and displayed a splash screen evertime I booted.  With some reading I figure DDO uses its own boot record that has to do with a solution to previous windows versions drive limitations.  So if grub hit this instead of the windows mbr with the ntldr do you think it would wiped out the partitions, being as the DDO boot record being overwritten might compimise the whole DDO configuration, or did my install just have a fluke accident or some other issue.  I have dual booted with mandrake 9.2, 10.1, Debian woody and sarge and never had either of them shanghia my windows drive so as I have reinstalled windows I am a bit apprehensive to try again until I get some other ideas besides my own guesses.

Thanks for any light you guys might be able to shred.

---

