---
title: "[SOLVED] Random freezing after libcdio6 update"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Pelham123 on 2008-02-22
Just posting this as an 'information' thread. After an update with libpcre3, libpcrecpp0 and libcdio6 i started getting random freezing that required hard reset. Couldnt boot into recovery mode, boot hanging at...

ata1: timeout waiting for ADMA IDLE, stat=0x440
ata1: timeout waiting for ADMA LEGACY, stat=0x440
ata1.00: exception Emask 0x1 SAct 0x0 SErr 0x100000 action 0x2
ata1.00: (CPB resp_flags 0x11: CMD error)

Subsequent googling & bug searching led to IDE/ATA errors. None of the fixes worked for me. So I unplugged the CD IDE cable from the motherboard - no more random freezing :) Am guessing that libcdio6 is the problem as synaptic definition is 

**libcdio6_0.76-1ubuntu2.7.10.1_i386.deb** *This library is to encapsulate CD-ROM reading and control.*

Have posted bug report [https://bugs.launchpad.net/ubuntu/+source/libcdio/+bug/194527](https://bugs.launchpad.net/ubuntu/+source/libcdio/+bug/194527)

---

### Post by gimfred on 2008-02-25
Thanks for the heads up :)

---

### Post by Pelham123 on 2008-02-27
Just an update.

1) Random freezes after libcdio6 update
2) Rebooting after removing IDE CD cd-drive cable stopped freezing of system
3) Rebooting again with IDE cd-drive plugged in -> no more freezing of system

Therefore some initial conflict with drive, removing somehow reset hardware detection(?) and now everything is good..so far ;)

---

