---
title: "Installing backtrack OS has stopped windows 7 booting"
date: 2011-12-18
forum: Any Other OS
---

### Post by tylergard702 on 2011-12-18
I was trying to install backtrack OS to my primary hard drive (along side Windows 7) and at 99% of copying files the setup reported there was not sufficient memory to install backtrack. I cannot boot back into windows 7 as the computer resets before getting past the boot screen (shows 'starting windows' as normal then the screen blacks and takes me back to BIOS).
this process loops unless I select windows repair option, which does not fix the problem.
The Backtrack live CD won't let me delete the new, half-installed partition, so therefore I cannot change the windows partition back to it's usual (small) size of 55GB.

All help would be appreciated as I need windows on my PC for work (else I would use linux full time :( )

Thank you to all in advance. :D

---

### Post by Buntumatic on 2011-12-18
Not sure what Backtrack Linux and Windows has to do with Ubuntu.
Nevertheless, the best ever dualboot scheme with Windows is to have Windows on secondary hard drive. Then, every time you need to reinstall it just disconnect the primary drive and reinstall.
Out of curiosity, what software it is that doesn't run in Wine?

---

### Post by tylergard702 on 2011-12-19
Thank you for the reply.
Sorry about that, I had a Linux problem and presumed I should post it here.
I only have one 60GB(55GB) Hard Drive in my laptop, and it only takes one :(, nevertheless, I may be getting a desktop soon and will probably have two 1TB hard drives. I will bear this scheme in mind :).
I use windows for work because I much prefer Microsoft office to open office and I have never managed to set up wine to emulate Microsoft office (or any other Microsoft program at that matter).
Also Java won't run in wine emulated programs and therefore windows seems essential to run all my programs :(.
I am going to use a Ubuntu live CD, as I like the partition manager it offers, and then try to fix my problem from there.
Thank you for your reply and helpful scheme,
Guess I shouldn't have messed around with the partitions, especially knowing how much of a 'control freak' windows is when it comes to resizing partitions.
Thank you for the help,
tylergard702

---

### Post by oldos2er on 2011-12-19
Moved to Other OS/Distro Talk

---

### Post by CJ-1990 on 2011-12-20
G'day dood, my name is CJ :)

I'm kind of new to linux but from my newly found knowledge it seems as though when you've gone to install Backtrack to a new partition on the same drive as your windows OS, you've somehow overwritten part of the windows drive, now the part that has been overwritten doesn't have to be an important part, any change in the windows OS will cause the computer to panic not being able to find the complete part... 

If it is just a boot problem, maybe you've overwritten the MBR of the drive with the grub loader for BT.


A bit of advice, when dual-booting, it's always recommended to manually configure the partitions and leave atleast 1gb of space between OS' in case of this happening...

Backtrack is not meant to be installed on a HDD internally or externally, it's meant to be run from a live-cd environment, however, if you do install it to a drive, which I have, install it to a separate drive, as BT is a specifically designed OS, not to be mixed with an every day OS, also, wordlists take up a hell of alot of room, one of mine is upwards of 20gb...


I hope I have helped even a little bit, and hope that your problem is sorted soon 8) Much luck with your Linux endeavours

Cheers

CJ

---

