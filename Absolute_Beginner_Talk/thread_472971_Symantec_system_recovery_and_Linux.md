---
title: "Symantec system recovery and Linux"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by willl on 2007-06-13
I have a laptop that is a couple years old now and came from the factory installed with Symantec System Recovery, and of course Win XP. This Symantec app entails (I think) a separate partition on which a backup of the factory installed OS, drivers, and software reside so that you can boot into a recovery console and restore the machine to its original factory state.

My question is, if I install Linux over the windows partition, while leaving the Symantec system recover partition alone, will I be able to still boot into the recovery and restore to factory state?

---

### Post by dpar on 2007-06-13
I doubt it, but I'm no expert.:biggrin:

---

### Post by starcraft.man on 2007-06-13
> **willl said:**
> 
My question is, if I install Linux over the windows partition, while leaving the Symantec system recover partition alone, will I be able to still boot into the recovery and restore to factory state?

Yes, but its conditional. My IBM had a restore partition like that, and it was accessed via the BIOS menu (I pushed enter and had options, one was to restore factory install and other was BIOS utility). As long as you access this partition via a menu embedded in the BIOS and not in any feature tied to the Windows install, you will be fine. Also, you can usually make a bootable disk from those partitions, you should investigate that possibility. 

Just make sure not to wipe the partition with your factory partition, then your hosed.

---

### Post by reckless2k2 on 2007-06-13
a few things.......this is possible if you have the emergency boot media to access the recovery partition. many times you have to create it inside windows first before you "have" it in your hands. i'm not sure of your situation. also, many of these recovery systems allow you to burn the contents of the recovery partition to media (cd or dvd) in the event that you decide to free that recovery partition for more space. you really have to consult your pc docs and or the docs for that program to answer many of these questions. 

i had to create the recovery boot media to access the recovery partition if i blew EVERYTHING away and or only left the recovery partition. in most cases when i came across systems and or my own with this recovery partition, i usually backed ALL of it up to media if given the option in the event i blew the whole drive away.

---

