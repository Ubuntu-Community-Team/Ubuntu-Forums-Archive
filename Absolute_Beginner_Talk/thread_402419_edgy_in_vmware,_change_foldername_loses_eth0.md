---
title: "edgy in vmware, change foldername loses eth0"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by DerDen on 2007-04-05
Hello All!

For test purposes I run Ubuntu server in vmware player. It all works fine, but when i change the name of the folder in which the vmware is (so this is the folder on the host machine(windows XP)) I lose insite the guest machine (the ubuntu server) my ethernet card. It simply is not visible anymore when i give the command 'ifconfig'.
When I change the foldername back and restart the guest machine the eth0 is there again.

My eth0 in the guest machine is 'bridged' to my phisical ethernet card.

Exactly the same situatuation when I move the machine to another folder.

Anyone an idea?

thanks in advace!!!!!!!!

---

### Post by DerDen on 2007-04-06
It is solved, I found an answer in the vmware forum... but I'll post the answer here as well, in case anyone else runs into the same issue:

The Fix: 

in guest machine:
ifconfig -a 
the "new" ethernet adapter may show up as eth1 

write down the mac address: nn:nn:nn:nn:nn 

cd /etc/ 
sudo vim iftab 

change the existing mac address to your "new" ethernet adapter MAC address... 

reboot the guest OS.

---

