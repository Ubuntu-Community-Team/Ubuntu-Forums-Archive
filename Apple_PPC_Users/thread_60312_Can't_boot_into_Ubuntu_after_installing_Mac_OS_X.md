---
title: "Can't boot into Ubuntu after installing Mac OS X"
date: 2005-08-27
forum: Apple PPC Users
---

### Post by star-affinity on 2005-08-27
I have Ubuntu installed on a PowerBook G4.
One partition is used for Mac OS X. When I installed Ubuntu I could successfully boot into Linux. After installing OS X it always booted into OS X, so I held down the "alt/option" key during boot to get to the startup manager wher I can choose the Linux partition. Then yaboot comes up, but pressing "L" just takes me to another prompt where I can type "help" to get up "Linux" and "old". If I type "Linux" I come to the Open Firmware prompt (white background with black text).

How do I do to get back into Linux and set things up so I can dual boot with ease?

---

### Post by gruepig on 2005-08-29
Kinda strange, but try this.  In Open Firmware, type 'boot hd:,yaboot'.  Hopefully that will boot Ubuntu.

(If that works, you should check your partition table with 'fdisk /dev/hda'.  I think the bootstrap partition needs to be before the OS X partition.  Then check /etc/yaboot.conf to make sure all your partition numbers are correct.  To reinstall the bootloader, run 'sudo mkofboot -b /dev/hdaX', where X is the number of the bootstrap partition.)

---

### Post by danns on 2005-08-29
I believe if you hold in the option key during the boot you will be provided with a number of boot partitions/devices that were found.  You should see a Tux icon in there along with your regular boot choices.  

I've had this problem in the past and that is how I solved it.  I'm pretty sure it is the option key.

---

