---
title: "getting the internet working"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by kickstart on 2007-08-11
I just did a fresh install of Fiesty and it seems as if it does not recognise my network adaptor. I have both Realtek RTL8111/8168B PCI Express Gigabit Ethernet Controller and a RTL-8139/8139C/8139C+ (this is the one built into my motherboard obviously).

If i type 'ifconfig' i only get 'lo' which seems to me that Ubuntu has not recognised either my onboard NIC or my PCI NIC. 

NOW, here is the really strange part. I had Ubuntu on this computerjust yesterday and on that particular install, both NIC's were recognised on my first start up, i just had to type in 'sudo ifdown etho0' etc etc to get it working.

Has anyone got any ideas as to why this time my network cards are not recognised and HOW can i get them working so i can get back on the internet on that computer?

Cheers.

Kickstart

---

### Post by kickstart on 2007-08-12
do you think its possible that there has been an error whilst installing this time around?

---

### Post by kickstart on 2007-08-12
ok well i have an update for anyone who might be reading this and can help.

i have got the cd that came with the PCI Express Card, and it has the realtek NP1100 drives on it, for Linux.

However i have no idea how to install these drivers?

any pointers?

---

### Post by Austin_KW on 2007-08-12
> **kickstart said:**
> ok well i have an update for anyone who might be reading this and can help.

i have got the cd that came with the PCI Express Card, and it has the realtek NP1100 drives on it, for Linux.

However i have no idea how to install these drivers?

any pointers?

Have a read of the man pages for insmod and modprobe, enter the following in a terminal;
man insmod
man modprobe

You may be able to just "sudo insmod /path/driveName.ko", you would have to do this every time you boot. 
modprobe loads modules by name from /lib/modules/kernelVersion/

---

