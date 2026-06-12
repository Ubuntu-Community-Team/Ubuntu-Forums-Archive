---
title: "Need help for installation, MacbookAir3,2"
date: 2012-09-16
forum: Apple Hardware Users
---

### Post by shawnlyu on 2012-09-16
Hi guys
I'm new to Ubuntu. I got a MacbookAir3,2 (Late 2010 13') using Mountain Lion. 
I followed this thread:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
&#8226; I paid attention to entering "nomodeset" mode upon "try Ubuntu".
&#8226; During the installation I created a 2G swap partition and another root partition. 
&#8226; I installed the boot loader to the root partition of Linux.
Still I got the partition table problem --- rEFIt won't sync the partition table. The exact error is:

```
Status: Analysis inconclusive, will not touch this disk.
Error: Not Found returned from gptsync.efi

```

Then I followed this thread to solve that one:
[http://ubuntuforums.org/showpost.php?p=11215214&postcount=185](http://ubuntuforums.org/showpost.php?p=11215214&postcount=185)
* Different from the author of that thread, I didn't see the "Recovery HD" partition while using gdisk. Still I followed the instructions.
After that I rebooted the Mac and it hanged at Tux. Another couple reboots, still hanging&#8230;

Then I knew I may need some help from you experts. Here is my partition table under rEFIt.

```
Current GPT partition table:
#	Start LBA	End LBA		Type
1	409640		170309735	Mac OS X HFS+
2	170311680	174505983	Linux Swap
3	174505984	236976127	Basic Data

Current MBR partition table:
# A	Start LBA	End LBA		Type
1	1		409639		EE EFI Protective
2	409640		170309735	AF Mac OS X HFS+
3	170311680	174505983	82 Linux swap / Solaris
4 *	174505984	236976127	83 Linux

Status: Analysis inconclusive, will not touch this disk.
Error: Not Found returned from gptsync.efi
```

I've worked from Friday night till today to install a Linux on my Mac but no success. I've tried SUSE 12.2 and Ubuntu 12.04, no success, I'm right now extremely frustrated and tired. Hope someone can help. I used SUSE on my old PC before, but didn't expect Linux on Mac to be this hard.

Thank you guys, I'm waiting for your kind reply!

---

