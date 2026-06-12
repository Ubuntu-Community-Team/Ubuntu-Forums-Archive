---
title: "Dual G5 yaboot or partitioning problems"
date: 2006-10-31
forum: Apple PPC Users
---

### Post by redbaritone on 2006-10-31
Okay, I've gotten the same results TWICE, now, so I thought I'd at least warn others, and hopefully get some direction on where to go  from here.

I cloned my hard drive, first. Then booted from an external drive and repartitioned my internal drive into two partitions: the first as hfs+ journaled to contain Mac OSX. The second as "free space".

Then, I booted the Edgy Live CD and told it to install onto the largest free space available. It came up saying that it would create partition #4 on SCSI1 (sda) (BTW, I don't have a SCSI drive!) as ext3 and partition #5 on the same drive as swap. I continued, and it appeared to work correctly.

Upon reboot, it ejects the CD and asks you to remove the CD, close the tray and then press "Enter". I did, and nothing happens. I connected another USB keyboard, just to make sure it wasn't the one I was using (a Matias Tactile Pro, configured as standard US keyboard). Again, nothing happened, but I suspect it's because it's not going to load ANY USB drivers at that point. Anyway, I pressed and held the power button on my G5 to force a shutdown, then restarted it. It loaded Mac OSX, on my first partition, normally - without going through yaboot. I restarted and held down the option key to allow me to choose the boot volume. I chose the linux partition, and it then loads yaboot.

Neither the (l)inux or (x) MacOSX option works. The "c" (CD) option works, but only if you reboot into open firmware and load the CD after doing: "eject cd". Also, if I reboot, it brings up yaboot (by default now), so I can't get into Mac OSX OR Kubuntu.

So, unless I boot the live CD, my system is hosed. I realize that my yaboot is messed up, but I have no idea how to fix it from the liveCD. At this point yesterday, I tried to mount /dev/sda#, where # is the partition number. I can't remember exactly what happened but it said something about not being able to load "unionfs". 

If someone could _step_ me through how to fix this, I'd really appreciate it. Otherwise, I'm going to have to repartition my drive (a third time) and forget about Kubuntu. This is on my work machine, and I'm wasting time screwing around with this.

 ](*,) 

Thanks,
Doug

---

