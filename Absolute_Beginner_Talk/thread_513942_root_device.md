---
title: "root device"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-07-31
How do I know about my root device as to which one is it. I have one hard drive , 80 GB with XP and Ubuntu 7.04. I want to make a bootable CD for which I need to know the root device(/dev/hda1 or /dev/hda2 etc.) I tried using both but none of them boots up. is there any other root device?
Thanks

---

### Post by hyper_ch on 2007-07-31
Well, start Ubuntu, open a terminal and then enter:

```

df -l

```

The partition that will show up mounted as "/" is your root:

e.g.
> 
Filesystem           1K-blocks      Used Available Use% Mounted on
**/dev/sda3             28834744   4973344  22396676  19% /**
varrun                  517372       300    517072   1% /var/run
varlock                 517372         0    517372   0% /var/lock
procbususb              517372       152    517220   1% /proc/bus/usb
udev                    517372       152    517220   1% /dev
devshm                  517372         0    517372   0% /dev/shm
lrm                     517372     33788    483584   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda4            418765640 357701392  39792180  90% /home
/dev/sda1             30716248   6882660  23833588  23% /media/sda1
/dev/sdb1            307663800 200386244  97900504  68% /media/sdb1
/dev/mapper/hda1     153834336 120884976  25134972  83% /media/hda1
/dev/mapper/hdd1     118169360  97944140  14222564  88% /media/hdd1


---

