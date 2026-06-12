---
title: "steam in wine - not enough disk space?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-07-02
I am running wine 0.9.40 in ubuntu 7.04.

I installed steam, then installed through it half life, counterstrike & counterstrike source.

However, whenever I try and install anything else, it says I do not have enough disk space. Despite having ~70GB free. I checked in winecfg and it lists drives as:

C: ../drive_c
D: /media/cdrom0
E: /media/IPOD (irrelavent but yeh...)
H: /home/daniel
Z: / 

Any clues?

(also, sorry if I shouldn't be posting wine stuff here :( )

---

### Post by dfreer on 2007-07-02
what does df -h report?

---

### Post by moredhel on 2007-07-03
sorry for the delay:

Filesystem            Size Used Avail Use% Mounted on
/dev/hdc1             106G   37G   65G  36% /
varrun                760M  228K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb            760M  136K  760M   1% /proc/bus/usb
udev                  760M  136K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   33M  727M   5% /lib/modules/2.6.20-16-generic/volatile
/dev/hdd1              75G   37G   38G  50% /media/disk

---

### Post by moredhel on 2007-07-03
bump?

---

### Post by dfreer on 2007-07-04
You could try rolling back to a older wine release, I dunno why wine is complaining about hard drive space.

---

