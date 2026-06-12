---
title: "Problems booting alternate cd on iMac G3"
date: 2007-12-24
forum: Apple PPC Users
---

### Post by codecrazy on 2007-12-24
I have a tray-loading iMac G3, and I decided to give it an upgrade to Ubuntu Feisty. The problem is that whenever I try to boot from the alternate CD, I get what looks like an Apple Open Firmware prompt (it says Apple Open Firmware at the top). What should I do :confused:? Any tips would be appreciated.

---

### Post by jayseye on 2008-01-01
Have you confirmed that a tray-loading iMac meets the minimum requirements for Feisty? 
 
On a slot-loading iMac G3 DV, with the 7.10 Gutsy Desktop Live CD, I was able to avoid getting stuck at Open Firmware by typing this at the Boot prompt: 
 
 live-nosplash-powerpc video=ofonly 
 
per this page:  
 
 [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) 

However, that just got me to a BusyBox prompt, and I'm still working through the next steps there.

---

### Post by codecrazy on 2008-01-02
I just go through to the yaboot prompt by typing "boot hd:2,yaboot" in the open firmware prompt (by holding down option+apple+o+f at startup, not by trying to boot from the cd). I got to the alternate installer, but I then realized that the partiton that I wanted to resize was an hfs+ partiton. Resizing that type "hasn't been implemented yet". I then tried to boot into mac os 9.2 to see if I could resize the partition from there. When I tried to boot into it, I got a floppy disk icon with a flashing "?" in the middle. I knew this meant there was no startup disk selected, so I booted into an os 9 CD. It then told me that the drive was unmounted. I don't want to erase all of my data by initializing it, so is there any other way to mount the hard drive through the OF prompt or something?

---

### Post by jayseye on 2008-01-04
Thanks for the boot command syntax. Gutsy's GUI "Partition Editor"  **GParted** can shrink HFS+ partitions, if you can boot Gutsy's Desktop Live CD. So if you can run Gutsy's Alternate Install CD, presumably the command-line **parted** would also allow shrinking HFS+. 
 
Otherwise Mac OS X command-line tools reportedly can shrink an HFS+ partition, but that seems complex and risky. OSX GUI **Disk Utility** only does destructive partitioning, but commercial programs like Drive Genius claim non-destructive resizing. 
 
After shrinking the partition using Gutsy, Feisty may be better for you: since my previous post here, I've found major issues reported for Gutsy PPC, especially with older Macs. 
 
To answer your question, I'd be amazed if OS 9 could resize an HFS+ partition. If it could, then you'd probably need it unmounted anyway. GParted forces you to unmount a partition before changing it in any way. In any case, you'll need to turn off Journalling (using Disk Utility) before shrinking a volume.

---

