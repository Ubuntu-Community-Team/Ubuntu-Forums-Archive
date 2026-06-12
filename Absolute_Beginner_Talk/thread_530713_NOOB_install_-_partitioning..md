---
title: "NOOB install - partitioning."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by __lonewolf on 2007-08-20
Hello,
   I am a new user to ubuntu, but I have a little experience with playing with Linux and using unix a bit a work ( I probably know enough to get myself in deep doo-doo :) ).  This is how I have the ubuntu install partitioned, went with the default for splitting up everything onto different devices (read somewhere that is good to do on a large (160GB) disk).

The other day, the '/' partition was reading 100%.  After a bit and running 'sudo apt-get clean', it is now at the state you see here.  Should I look at redoing the install to make '/' bigger or is the default ok?   The pc is being used for a family pc.  

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             274M  252M  7.5M  98% /
varrun                880M  100K  880M   1% /var/run
varlock               880M     0  880M   0% /var/lock
procbususb            880M  140K  880M   1% /proc/bus/usb
udev                  880M  140K  880M   1% /dev
devshm                880M     0  880M   0% /dev/shm
lrm                   880M   39M  842M   5% /lib/modules/2.6.20-16-generic/volatile
/dev/sda9             133G   17G  110G  14% /home
/dev/sda8             373M   11M  343M   3% /tmp
/dev/sda5             5.5G  2.1G  3.2G  40% /usr
/dev/sda6             2.8G  261M  2.4G  10% /var
/dev/hda5              58G   31G   27G  54% /media/disk


Thanks,
__LoneWolf

---

### Post by macogw on 2007-08-20
OH MY!  You don't need to split so much up.  All under / is ok, but many put /home separate for easier reinstalls.  On servers /var is also separate so that logs don't flood / and some put /usr separate to save installed programs during a reinstall.  Dividing up things smaller than that is totally unnecessary.

I do 10GB for /
1GB swap
the rest /home

On my comp with a tiny (5GB) hard drive where I was worried that / could fill up, I made / like 2GB and /var 1GB or something like that.  2GB is only because I wasn't going to be installing much of anything and knew I could get away with it (enlightenment, firefox, and open office are the only things on there).

---

