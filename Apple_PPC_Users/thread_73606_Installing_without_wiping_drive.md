---
title: "Installing without wiping drive"
date: 2005-10-09
forum: Apple PPC Users
---

### Post by a.mcfarlane on 2005-10-09
Hi all,

I'm interested in installing Unbuntu, but I don't particularily want to wipe my drive clean, as I don't have an external drive to backup to, and backing up 60GB via CD's is simply too daunting.

Is there a way to resize my partition map so as to free up space for a new partition on which I can install Unbuntu?

I'm running 10.4.2 on an iBook G4, 80GB HD.  Thanks in advance.

---

### Post by aysiu on 2005-10-09
Have you seen this?

[https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot?highlight=%28powerpc%29](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot?highlight=%28powerpc%29)

---

### Post by a.mcfarlane on 2005-10-09
That doesn't particularily answer my question.  I'm aware that I can operate two seperate operating systems on a single computer using a bootloader, but what I'm wondering if if there is a safe (read: no backup required) way to partition my drive without wiping it clean first.

---

### Post by Joe_lurker on 2005-10-10
You can resize your hard drive using a program such as Gnuparted ([http://www.gnu.org/software/parted/parted.html)](http://www.gnu.org/software/parted/parted.html)).  There are also several other programs such as QtParted that have a more user-friendly front end.  I am not sure if either of these are included in the live cd or not.

A couple of notes:
You will need to boot to the Mac OS X install cd and choose disk tools from the menu and disable journaling on the partition.
You cannot move the partiton just resize it.  ie. the start of the partition must remain the same.
USE AT YOUR OWN RISK!  Make sure to backup any important data before hand.

-Joe

---

### Post by beewer on 2005-10-13
[QUOTE=Joe_lurker]You can resize your hard drive using a program such as Gnuparted ([http://www.gnu.org/software/parted/parted.html)](http://www.gnu.org/software/parted/parted.html)).  There are also several other programs such as QtParted that have a more user-friendly front end.  I am not sure if either of these are included in the live cd or not.
.
.
.
[/QUOTE]

Hi.

I am also interested in installing Ubuntu to my 1.33Ghz G4 iBook. Please post your experiences here. I was previously instructed to install mac os x to firewire drive and then repartitioning internal hd but this is not an option to me since I don't have fw-drive ;)

---

