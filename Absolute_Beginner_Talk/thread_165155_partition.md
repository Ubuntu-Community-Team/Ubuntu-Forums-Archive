---
title: "partition"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by greenwoodman on 2006-04-24
if I partitioned my drive, how do I boot with windows XP again?

---

### Post by nalmeth on 2006-04-24
if you only partitioned so far, I don't see why you wouldn't be able to boot XP.
Have you installed ubuntu? 
Are you actually unable to boot XP?
More info

---

### Post by Bartender on 2006-04-24
greenwood -
Are you just looking for some ideas before taking the plunge?  Google hermanzone, check out his instructions for dual-booting.  
Are you wondering how it works once you've done the deed?  My test PC is running W2K and Breezy.  When I start it up, I get the usual BIOS-related screens, then a DOS-looking screen which gives me a list of options.  This screen is the interface for GRUB, the program (well, one of them actually but let's keep this simple) that handles multiple-booting chores.  You'll see Ubuntu first on the list, and if you do nothing the PC will start booting to Ubuntu in - um - five or ten seconds, don't remember which.  You have several other options on the GRUB screen.  If you want your Windows partition, you just tap the "down" key until you get to the Windows line, then hit "Enter".

Easy

---

### Post by MasonM on 2006-04-24
Assuming you partition correctly and don't wipe out the Xp partition (common mistake), once the bootloader Grub is installed you will be presented with the option to either boot into Ubuntu or Windows.

---

