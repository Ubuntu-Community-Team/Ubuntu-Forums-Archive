---
title: "Apple boot loader thingy"
date: 2006-06-30
forum: Apple PPC Users
---

### Post by bonniejonnie on 2006-06-30
Okay... trying to get Ubuntu to dual boot with OS X on my iBook G4.

So far I've managed to resize my Mac partition (via 'parted' via the Ubuntu terminal via the live CD) to 50GB leaving 10GB for Linux. Out of the remaining 10GB I've created two partitions, a root partition of 9ishGB and a swap partition of 1ishGB. I installed Ubuntu, selecting the relevant partitions and let the installer reformat these two partitions whatever way it wanted. Before installation began I was warned that no Apple Boot loader (or boot disk) partition could be found. I continued anyway but when the installation reached the end it error'd telling me again about not finding this Apple boot thingy.

So now I'm lost. There's a couple of other partitions (unviewable to Disk Utility) which I think might have something to do with booting, but not really sure.

What do I do now. Do I need to create another partition? Do I somehow need to get the Ubuntu installer to recognise a partition that's already there?

I don't want to do an entire reformat. I have no medium to back up to.

This is my first attempt at Linux... so please... be careful with me.

---

### Post by tidris on 2006-06-30
The easy way to go is to let the ubuntu installer create ALL the partitions it needs using the free space in the disk. In other words, delete the root and swap partitions you had created for ubuntu and try installing again, this time letting the installer automatically partition the free disk space.

---

### Post by Uta on 2006-06-30
That's good advice (tidris)! I resized my iBook's HD and left 10GB unallocated then let the Dapper installer use the free space (unallocated) and it worked perfectly.
It installed a bootloader and on restart it was "L" for linux "X" for macos or "C" for cd--
Reinstall Dapper. Good Luck.

---

### Post by bonniejonnie on 2006-07-01
Oh as simple as that is it? Okay... thanks... I'll give that a try to night.

Thanks again,

Jon.

---

