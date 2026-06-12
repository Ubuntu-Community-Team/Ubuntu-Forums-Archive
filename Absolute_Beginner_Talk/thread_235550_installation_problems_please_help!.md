---
title: "installation problems please help!"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by sleepmonsta on 2006-08-13
Hi everyone, apologies in advance for being a n00b, but I need some help.

I have partitioned my existing drive currently running xp with a new partition.

I have then booted via the ubuntu CD and have selected the OEM install. The install seems to go progress until it gets to the stage where it checks for existing drives. The install then just comes to a grinding halt and shows a blank blue screen.

It didnt prompt me at any stage to say which drive or partition to install to.

Any ideas?

---

### Post by taurus on 2006-08-13
Is it an EIDE, SATA, RAID, etc.?  A little more about the spec of your machine would be helpful...

---

### Post by MaximB on 2006-08-13
for a noob - don't use OEM install
install it normall install (that is after you manage to repait your hardware ;))

---

### Post by sleepmonsta on 2006-08-13
hi,
the machine is a amd 3200+ with a 120 gb SATA drive and 1 gb of RAM.

I did get ubuntu to install eventually from the live cd and immediately went through the update procedure.

After the update I could no longer boot up Ubuntu. The system hangs at mounting root file system and ecventually (after 5 minutes or so) goes to the command prompt.

Does anybody have any suggestions?

Many thanks

---

### Post by taurus on 2006-08-13
What does your /etc/fstab look like?

```

more /etc/fstab
sudo fdisk -l

```

---

### Post by sleepmonsta on 2006-08-13
i'm afraid you've lost me there! the system is currently at a command prompt . what should I type to look at /etc/fstab?
thanks in advance for your help. i'm new to linux so am a bit helpless!
thanks
ps there is an alert which says /dev/sda3 does not exist.

---

