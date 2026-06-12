---
title: "Partition Problem! / &quot;root&quot;  and /home writing to same partition!"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-10-23
I got a new laptop an i used GParted to set up the partitions, / "root", a swap partition, and a partition for everything else ie /home.

what i just noticed that for some reason ubuntu is writing everything saved in the /home to the / "root" partition.  the partition that  wanted to use for my home is showing up and the only thing in it is a locked folder: lost+found.

if i try to save anything to the directory /media/sda5 it says i do not have permission.

the properties of my /home says: Location /home   Volume:/ 

how would one go about removing /home from / and making sda5 the /home?

i'm not sure of what exact terminal command gives a nice layout of the partitions but i used "df" to start.  this is the output:

> 
alain@s15:~$ df
Filesystem           1K-blocks      Used        Available         Use%        Mounted on
/dev/sda7             5320936   2118704     2931940         42%       /
varrun                    452072       104           451968             1%         /var/run
varlock                   452072         0             452072             0%         /var/lock
procbususb           452072       120          451952             1%          /proc/bus/usb
udev                        452072       120          451952             1%         /dev
devshm                  452072         0             452072             0%        /dev/shm
lrm                           452072     33788        418284      8% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1               80120      7974            72146              10%         /media/sda1
/dev/sda2               9767516   9573440   194076            99%         /media/sda2
/dev/sda3               3142576   2256212   886364             72%        /media/sda3
/dev/sda5              95753548    192312   90697160           1%       /media/sda5



i'm just wondering whether i'll need to do another fresh install or if this is fixable.  if anyone needs more output let me know the commands and i'd be more than happy to throw it down, aswell as any text from any files.  

Thanks, Alain

---

### Post by S15_88 on 2007-10-23
i'm thinking a fresh install, T-minus 14 minutes, until then feel free to try and save me if you know of a way of fixing this problem!

Thanks, Alain

---

### Post by louieb on 2007-10-23
look here [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you do a reinstall you will have to use manual partitioning in order to have (mount) /home on its own partition.

---

