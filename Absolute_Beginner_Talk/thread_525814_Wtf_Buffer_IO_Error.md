---
title: "Wtf: Buffer I/O Error"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by ElliottMarlow on 2007-08-14
My question doesn't concern any particular problem, I am merely asking out of curiosity. When I boot up, I notice the following text:

[SIZE="1"][ 1783.724000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1783.772000] ISOFS: changing to secondary root
[ 1818.272000] sr 1:0:0:0: SCSI error: return code = 0x08000002
[ 1818.272000] sr0: Current: sense key: Medium Error
[ 1818.272000]     Additional sense: Random positioning error
[ 1818.272000] Info fld=0x2c6
[ 1818.272000] end_request: I/O error, dev sr0, sector 2840
[ 1818.272000] Buffer I/O error on device sr0, logical block 710
[ 1818.272000] Buffer I/O error on device sr0, logical block 711
[ 1818.272000] Buffer I/O error on device sr0, logical block 712
[ 1818.272000] Buffer I/O error on device sr0, logical block 713
[ 1818.272000] Buffer I/O error on device sr0, logical block 714
[ 1818.272000] Buffer I/O error on device sr0, logical block 715
[ 1818.272000] Buffer I/O error on device sr0, logical block 716
[ 1818.272000] Buffer I/O error on device sr0, logical block 717
[ 1818.272000] Buffer I/O error on device sr0, logical block 718
[ 1818.272000] Buffer I/O error on device sr0, logical block 719
[ 2665.492000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2665.496000] ISOFS: changing to secondary root[/SIZE]

First off, I only have Feisty 7.04 on my machine, so what exactly is "Microsoft Joliet Level 3"? I used to use XP, but when I installed Ubuntu I chose the format/total replacement option (whatever wipes your disk clean), so could this perhaps be something left over that needs to be removed?

Second, is Microsoft Joliet Level 3 causing the other errors? Does "medium error" indicate some level of severity? What about Buffer I/O error? Why does it repeat 10 times? I've been using Ubuntu now for over a month with no problems (other than my own ignorance), but should I expect problems to eventually result from whatever causes these errors?

---

### Post by Blutack on 2007-08-14
It is trying to read a disk of some sort.  The microsoft extensions are the way windows computers can display long file names on CDs, the linux equivilant is rockridge.  Your CD/DVD is maybe slightly scratched...other than that, no worries!

---

### Post by ElliottMarlow on 2007-08-15
> **Blutack said:**
> It is trying to read a disk of some sort.  The microsoft extensions are the way windows computers can display long file names on CDs, the linux equivilant is rockridge.  Your CD/DVD is maybe slightly scratched...other than that, no worries!

Hey thanks for your reply. Now that you mention it, I set my BIOS to boot from cd not long before installing Ubuntu. Do you think maybe those error messages could simply be the computer searching for a disc in the drive to boot from? Maybe it tries 10 times by default. I wonder if there is a way to change it to maybe 1 attempt?

---

