---
title: "Is it possible to achieve 3+1?"
date: 2007-07-07
forum: Apple Intel Users
---

### Post by michaels on 2007-07-07
Hi, guys!;)

I got a problem as follows: 

Currently, I've set up the triple boot system on my macbook pro, and I wanna boot another os from an external usb hard drive. As far as I know, to make the external hard drive bootable, it should be set a GUID. The biggest problem making me confused is whether this GUID of the external hard drive will also be recorded in GPT of EFI, so that it hurts the balance of the current GPT and MBR, making all the system crash?

Thank you!

---

### Post by ronocdh on 2007-07-07
> **michaels said:**
> Hi, guys!;)

I got a problem as follows: 

Currently, I've set up the triple boot system on my macbook pro, and I wanna boot another os from an external usb hard drive. As far as I know, to make the external hard drive bootable, it should be set a GUID. The biggest problem making me confused is whether this GUID of the external hard drive will also be recorded in GPT of EFI, so that it hurts the balance of the current GPT and MBR, making all the system crash?

Thank you!
I have never attempted to boot from an external drive with my MBP, so take this advice with a grain of salt. If you search through this forum, you should find numerous threads on booting from an external. I see no reason why it isn't possible to manage your 3+1 setup, as rEFIt should be able to find that option upon booting, provide you set it up however it's necessary to.

I think a workable analogy would be that you can boot from a CD, which in a way is 3+1, and so doesn't interfere with the partition limit on these EFI systems. I hope this helped, please keep us posted about your progress.

---

### Post by michaels on 2007-07-09
Thank you for your reply.

I've got the answer of my problem: the new external hard drive, which has been set a GUID, will not affact the whole triple boot system. Moreover, the rEFIt can easily but not so efficiently detect and boot from it.

P.S. The OS I tested is mac os x 10.5 Leopard, which is still a test release. If you're interested in it, use google to search "pirate bay the new big cat", and then you can get it! To tell the truth, leopard is slightly buggy, but worth trying and really amazing!!!

Good Luck!

---

### Post by grim1234 on 2007-07-09
Probably best if you don't advocate piracy, especially if not of MS products. 

:p

---

### Post by benanzo on 2007-07-09
It is not necessary to format the external drive as GPT in order to boot.  However, if you try to install OS X on *any* hard disk the installer will insist on creating the GPT otherwise it wont install.  The solution to this is to install it as normal then make a tarball of the entire system, move it to another disk, reformat the original external disk as MBR (so you can have as many logical partitions as you want) then decompress the OS X tarball onto the new MBR disk.  It will work just fine.  OS X does not technically require GPT.  GRUB will boot OS X from a MBR disk just fine.

---

