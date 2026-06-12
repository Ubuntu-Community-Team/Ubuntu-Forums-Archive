---
title: "fresh single-boot 10.04, gpt/mbr out of sync"
date: 2010-08-06
forum: Apple Hardware Users
---

### Post by walkerpett on 2010-08-06
Hi,

I have just completed a fresh single-boot install of Ubuntu 10.04 on my 4,1 Macbook.  I am following [[COLOR="Red"]these[/COLOR]]("http://mac.linux.be/content/single-boot-linux-without-delay") directions in order to reduce the delay during the boot process.  In order to do this, I need to make sure my GPT and MBR tables are in sync, but the output from rEFIt (boot CD) gives:

```
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1           2048         4095  GRUB2 BIOS Boot
 2           4096    224829439  Basic Data
 3      224829440    234440703  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1         4095  ee  EFI Protective
 2 *         4096    224829439  83  Linux
 3      224829440    234440703  82  Linux swap / Solaris

Status: Analysis inconclusive, will not touch this disk.
Error: Not Found returned from gptsync.efi
```

It seems my tables are out of sync (or something?)  The only thing I can think of is that it got messed up when I ran update-grub after editing /etc/default/grub to do verbose boot.  1. Why would that mess up my partition table? 2. How can I resync my tables?

---

### Post by utilitytrack on 2010-08-06
First time I hear these things from Mac user :))

---

### Post by iguard06 on 2010-09-29
I have the same error on my dual boot system....I haven't searched for an answer yet...

---

### Post by srs5694 on 2010-09-29
Your partition table looks OK to me (or at least, as "OK" as any hybrid MBR partition table -- by definition, hybrid MBRs violate the GPT specification). Partitions #2 and #3 both begin and end on the same sector number in both MBR and GPT, which is the important point. GPT partition #1 isn't in the MBR, but that's fine; and MBR partition #1 is the EFI protective partition, which is necessary and normal.

My suspicion is that the version of gptsync you're using is old and doesn't recognize the partition type code for GPT partition #1 (the BIOS Boot Partition). If possible, I recommend bypassing that step.

Another comment: Linux is perfectly happy booting from a conventional GPT-only disk, so from a Linux perspective, you're better off using a conventional protective (non-hybrid) MBR with your GPT. I don't know, however, how rEFIt or other Mac boot loaders react to such a configuration. If they require a hybrid MBR, you might be stuck with it. If you care to experiment, try using [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert the hybrid MBR back into a conventional MBR. You can do this by launching the program, typing "x" to enter the experts' menu, typing "n" to create the new protective MBR, and typing "w" to save your changes. Once this is done, do *not* run gptsync on the disk. I'd like to emphasize that I don't know if this will work; it could just cause problems, in which case you'll have to recreate the hybrid MBR. I'm curious about the results, since I'm seeing a lot of posts here about hybrid MBR problems; using a pure GPT configuration would fix many of those problems. I don't have an Intel-based Mac on which to test it myself, though.

---

