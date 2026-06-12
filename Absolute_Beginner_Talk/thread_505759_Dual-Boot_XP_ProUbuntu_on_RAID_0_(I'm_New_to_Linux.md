---
title: "Dual-Boot XP Pro/Ubuntu on RAID 0 (I'm New to Linux)"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Azn Tr14dz on 2007-07-20
I've read some of the Stickies in this site, and they are a great help, but I'm still having some trouble installing Ubuntu.  After booting from the Live CD, I choose Install.  (Choose English, City, Keyboard, etc.)  When It comes to choosing my Hard Drive, it shows 2 80GB Hard Drives.  But the problem is, both of those Hard Drives are in RAID 0.  I can't just choose 1.  

Sorry if I'm lost.  I've read the Stickies on how to Install Ubuntu, install in RAID 0, searched other members' threads, but I still don't know what I should do at this point.

Thanks,
-Azn

My Specs BTW:
AMD Athlon 64 3200+ @ 2.75Ghz
1GB (2x512Mb) GeIL DDR 421
DFI Lanparty UT nF4 Ultra-D
ATI Radeon X800XL (Overclocked)
2x80GB WD Caviar SATA RAID 0

Again, sorry if this question has been asked before, I've tried reading as many related Stickies/Threads, but I'm still pretty lost.

---

### Post by Azn Tr14dz on 2007-07-20
Anyone?

---

### Post by motin on 2007-08-15
I just found myself in the same situation as you. 

The information I have gathered are not yet enough to solve the issue, but nevertheless:

What I do know:

[LIST]
[*]Intel RAID is not hardware RAID, but software RAID, meaning that the OS's needs help to interpret the disks as RAID Arrays
[*]This in fact means that for example the Windows installer needs extra drivers loaded before installation can be done onto a RAID Array. This is kind of the same for Ubuntu
[*]Detailed instructions on how to install Ubuntu on a Intel "Fake" RAID array is found at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[*]By installing the package "dmraid" in Live CD mode and running "sudo dmraid -ay", then choosing to manually partition the drives, I can see the RAID array disk(s) and partitions.
[*]The RAID /dev/mapper/ entries are however illogically numbered and presented and it doesn't feel safe to change the partitions in the array
[*]The rest of the proposed procedure/instructions, however, (that are needed to have the system boot from a fake RAID array) are pretty complex for most beginners and even intermediate Linux users
[/LIST]

What I don't know:
[LIST]
[*]Someone talked about putting the /boot partition on non-raid (other sources also recommend putting the XP installation like this) - how do one use but say 80% of each of the disks for the array and have some space that are for normal disk partitions?
[*]Special to me as I am going to reinstall XP as well: Can I simply ignore the raid array configuration and partition the drives separately - or to I have to change the BIOS setup for this?
[/LIST]

Keep on searching for that solution mate!

Cheers

---

