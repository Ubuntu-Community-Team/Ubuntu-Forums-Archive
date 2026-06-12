---
title: "Live CD Runs On HP But Not Dell"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by rjacobsen on 2005-06-23
I posted a message a few days ago "Ubuntu Live Boot Problem" explaining that the Live CD I made will run and then stop at this point on my Dell Demension 8400:

Attached scsi removable disk sdc at scsi1, channel 0, id 0, lun 2

xmasstree suggested for me to use md5sum to check the CD and there were 2 files that had errors:

./install/netboot/pxelinux.cfg/default: FAILED open or read
./install/netboot/pxelinux.0: FAILED

In the command prompt the results showed up like this at the end:

c:\md5sum: WARNING: 1 of 1109 listed files cold not be read

c:\md5sum: WARNING: 1 of 1108 computed checksums did NOT match

I doawnloaded another iso file yesterday, burned a CD and it turned out the same way. I thought that maybe I should try the CDs on another computer so I got my old HP Pavillion laptop back from a friend, ran the CD on it and it works perfectly fine. Dell uses their own BIOS so I'm surmising there might be some kind of conflict. I also made a post "IRC CHAT" and betrayed suggested for me to get a pressed CD from ubuntu. I can use my laptop for now to play with ubuntu but my Dell is at least 3 times more powerful so it would work much better. If anyone has anymore suggestions, I would certainly appreciate it.
Thank You,
rjacobsen

---

