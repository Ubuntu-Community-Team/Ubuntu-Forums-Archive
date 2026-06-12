---
title: "ibook stops at installation with the following error..."
date: 2005-11-16
forum: Apple PPC Users
---

### Post by cmcgeecc on 2005-11-16
I've been trying to boot my ibook g3, but it won't read burned cd's.  So I decided to try to netboot it and I did everything that ninotab posted on the thread Original iMac- won't boot from cd.  I got it to boot from tftpboot but I get an error like this... "can't open device <cd:0>(next line) cd:-1,/install/boot.msg: Unable to open file, Invalid device"  So I realize that it was trying to boot from cd.  I think that when I mounted the iso to tftpboot dir that the iso was meant to boot from cd.  How do I get ahold of a network boot iso?  This is one of my questions cause it might solve the problem.

I also tried to manually boot the installation by typing in yaboot enet:192.168.0.2,install\powerpc\vmlinux because that's what it's trying to do from the cd, but then i get this error "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"  Any ideas as to how to fix this?

Thanks,
Chris

---

