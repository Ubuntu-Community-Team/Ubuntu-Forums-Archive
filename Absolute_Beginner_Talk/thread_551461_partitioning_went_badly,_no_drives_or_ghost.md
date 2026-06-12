---
title: "partitioning went badly, no drives or ghost"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by jskiff on 2007-09-15
I tried to install Ubuntu desktop 64bit 7.04 onto my drives (raid striping) after installing Acronis ghost software. I got a grub loading please wait message followed by an error 2 message. I could not boot anything so I reloaded XP, I needed internet connection to download an Acronis recovery CD. The Acronis wizard cannot find a drive. My promise raid driver software still sees the partition. Any ideas that might help with recovery. Thanks, Jim

---

### Post by Daveth on 2007-09-15
can I seek some clarity in this post please? You are attempting to dual boot Xp and Ubuntu, you have XP already installed, and you have a rat's nest of partitions and bits of linux scattered about. Do you have an Ubuntu live cd? I'm not sure where Ghost comes into it.

Your grub error 2 means "Bad file or directory type
This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. "

Whether this is a consequence of using Ghost i do not know. If you can clarify the current position then we can help out:)

---

### Post by cybersaurabh on 2007-09-15
reconfigure your boot loader

run ubuntu live cd
in terminal execute "sudo grub"
then "find /boot/grub/menu.lst"
it will return sumthing like (hd0,x)
x will be a number
make it root partition by
"root (hd0,x)"
then set boot loader at mbr by "setup (hd0)"
"quit"
restart your system

---

### Post by jskiff on 2007-09-15
> **Daveth said:**
> can I seek some clarity in this post please? You are attempting to dual boot Xp and Ubuntu, you have XP already installed, and you have a rat's nest of partitions and bits of linux scattered about. Do you have an Ubuntu live cd? I'm not sure where Ghost comes into it.

Your grub error 2 means "Bad file or directory type
This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. "

Whether this is a consequence of using Ghost i do not know. If you can clarify the current position then we can help out:)

Ok, Ghost comes into it because I can no longer access my original XP install/data files. My immediate concern of course is to recover my lost data. I thought the ghost would protect me from this mess.  I can work on the dual boot xp/ubuntu later. 
Yes I probably have a rats nest of partitions because even my XP install disc would not run in repair mode. It took out a partition - presumably a linux partition, before I could install XP. 
Yes I do have a live CD. 
Do you think my data might still be recoverable? I have tried to get help from Acronis but they have not responded at this point. I hope this helps.

---

### Post by jskiff on 2007-09-15
Do you think it might be too late to recover using this method (Boot loader repair)? The XP install that I used to reach this forum deleted a partition while installing. I might not have the Linux partition anymore. Or did it delete my ghost partition? What a mess. Is there any way to look at a partition to see what it is?

---

### Post by Daveth on 2007-09-15
yes, I think your data is probably just sitting there unless that partition delete hit the "wrong" one. You could try cybersaurabh's grub repair and see what happens- it will not take a sec to do, but I worry that your rat's nest will haunt you, even if you get back in.

If you have a live cd, set your cd drive to boot from that first (alter the BIOS setting), then fire it up, and load gparted from the repositories, and see what the lie of the land is. You can always take a screenshot and post it here if you do not understand what it tells you- someone can always interpret.

This handy guide might be worth browsing beforehand

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

- I'm off for pilau rice and samosas now, but will pop back later.

---

