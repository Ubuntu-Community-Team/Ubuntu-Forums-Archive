---
title: "Can't mount my DVD!"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-08-18
Hi there,

I need to install a game  on Ubuntu but Ubuntu  won't read the DVD! :(

I get the following error
> 
Invalid mount option when attempting to mount the volume 'CNC3'

This command "dmesg | tail" gives this output:
> 
rudolf@rh:~$ dmesg | tail
[   49.330309] /dev/vmnet: open called by PID 6254 (vmnet-dhcpd)
[   49.330516] /dev/vmnet: port on hub 8 successfully opened
[   49.816223] /dev/vmnet: open called by PID 6265 (vmnet-dhcpd)
[   49.816496] /dev/vmnet: port on hub 1 successfully opened
[   75.759688] cdrom: sr0: mrw address space DMA selected
[   75.811740] cdrom: sr0: mrw address space DMA selected
[   75.916453] Unable to identify CD-ROM format.
[  149.112928] cdrom: sr0: mrw address space DMA selected
[  149.161900] cdrom: sr0: mrw address space DMA selected
[  149.258672] Unable to identify CD-ROM format.


Please help! :)

Thanks,

Rudolf


PS: How can I mount a dvd drive manually or rip an ISO in WIndows?

---

### Post by RudolfMDLT on 2007-08-18
Very weird! K3B is ripping an ISO but Ubuntu can't read the DVD????

How can I mount this ISO in a Folder?

---

### Post by Amazona aestiva on 2007-08-22
1.Open terminal
2.Type this for mount: (change the pass to vaild)
```
sudo mount -o loop /Data/something.iso /mnt/destination
```
/mnt/destination can be /media/cdrom0
3.Type this for unmount:
```
sudo umount /media/iso
```
/media/iso must be where you mounted the .iso

---

