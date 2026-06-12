---
title: "Installing onto another drive (again)"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by dry_druid on 2006-09-18
I've been reading the messages on installing to a different hard drive and they go some way to explaining what's not working, but there doesn't appear to be anything which will really help this complete beginner.

I have windows XP on an IDE RAID mirror (2 partitions, C: & D: ) but want to put Ubuntu onto my SATA.  The SATA has two partitions (M: & N: ), one with stuff on (M: ), the other empty.  The live CD does its business and uses the empty partition but, as everyone else has experienced, reboots into windows.

What do I do to be able to dual boot without falling into the sorts of traps that have required others to fix their MBRs as well as jump through all sorts of hoops?

Thanks

---

### Post by bulldog on 2006-09-18
Put GRUB on the sata disk.

So you can select your boot device by hitting F11 or something like that.
[you can see at bootup at the bottom of your screen]

I imagine you have a recent MoBo then this should be possible.

I'm not an expert about raid configs,can't say anything about it that makes any sense

---

### Post by dry_druid on 2006-09-18
Thanks Bulldog.

Perhaps I should have said that the current boot disk is the IDE RAID - how will putting grub on the SATA drive help and how do I do that anyway?

---

### Post by bulldog on 2006-09-18
Will you use your raid config while you using Ubuntu?

Iff not disable the raid-drives and install Ubuntu on the Sata disk.
Because there are no other drives visible GRUB will be placed on the sata disk mbr.

After the install attach your raid config again so you can boot it.

If you want to use Ubuntu you have to push F11 or something mentioned before,to boot from your sata drive.

I'm not sure if you can mount your raid drives safely to Ubuntu though.

---

### Post by dry_druid on 2006-09-19
Sorry Bulldog, that didn't work.

---

### Post by bulldog on 2006-09-19
How's that?

What didn't work?

Is your raid config spoiling it all?

Think so because if I know something about raid configs it's controlled by the BIOS.

Didn't know though if you should have the possebillity to boot a separate drive.

Learned some,but it's a pity though.:sad:

---

### Post by dry_druid on 2006-09-19
As suggested, I disconnected all my drives except the SATA and installed from the live cd.  Wouldn't reboot at all.  Changed the BIOS to boot from the SATA and got grub error 22.  Reconnected my RAID (changed the BIOS back) and did F11/F8 but only windows present in the OS list.

---

