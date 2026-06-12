---
title: "[SOLVED] Run out of space"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-08
Hi,

I have 3 partitions on an 80GB disk:

/ 4GB
/home 70GB
swap 1GB

I want to merge / and home so that they are one partition - is that possible? I need to do it from the command line or webmin as I have no GUI installed.

Thanks.

---

### Post by scxtt on 2007-09-08
the lack of a GUI is irrelevant, since you can't do it from w/in the system anyway - you'd have to do it via a LiveCD ... how much of /home are you using?  actually, a **df -h** would be a good idea to add to this thread.

---

### Post by keymoo on 2007-09-08
Here's output from df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             3.7G  3.7G     0 100% /
varrun                506M  176K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   68K  506M   1% /proc/bus/usb
udev                  506M   68K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/hda3              69G  180M   66G   1% /home
/dev/sda1             459G   55G  381G  13% /var/lib/backuppc
```

---

### Post by az on 2007-09-08
Back up all of hda3 somewhere.  Delete hda3.  make hda2 bigger (use all the free space)  Make sure you extend the filesystem, too.  Create a /home folder in the / directory.  copy all your stuff you backed up from hda3 there.  Get rid of the /home fstab entry.  Reboot.

---

### Post by keymoo on 2007-09-09
Thanks I ran into all sorts of problems that alienates newbies like myself so I rebuilt the server - all is well now.

---

### Post by arai on 2007-09-09
this is the output from my system

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6             9.1G  2.5G  6.2G  29% /
varrun                505M   76K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
procbususb             10M  120K  9.9M   2% /proc/bus/usb
udev                   10M  120K  9.9M   2% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   18M  488M   4% /lib/modules/2.6.17-12-generic/volatile

```I have the same problem but the only difference is i want to increase the space used by ubuntu (current usage 10 gb). i don't want to completely erase the space used by windows (40 gb). i have _more than 10 gb of unused space in windows_. i want to utilize it for ubuntu. how to do this ?

---

### Post by scxtt on 2007-09-09
> **keymoo said:**
> Thanks I ran into all sorts of problems that [color=red]**alienates newbies like myself**[/color] so I rebuilt the server - all is well now.what?

---

### Post by scxtt on 2007-09-09
> **arai said:**
> this is the output from my system

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6             9.1G  2.5G  6.2G  29% /
varrun                505M   76K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
procbususb             10M  120K  9.9M   2% /proc/bus/usb
udev                   10M  120K  9.9M   2% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   18M  488M   4% /lib/modules/2.6.17-12-generic/volatile

```I have the same problem but the only difference is i want to increase the space used by ubuntu (current usage 10 gb). i don't want to completely erase the space used by windows (40 gb). i have _more than 10 gb of unused space in windows_. i want to utilize it for ubuntu. how to do this ?Gparted should be able to do this, reboot into a LiveCD and see if it'll let you resize your windows partition (make sure NO partitions are mounted when you're in the LiveCD environment).

---

### Post by arai on 2007-09-09
scxtt, i will update here. if i could change the partition succesfully using gparted. thanks.

Update : I have the this problem grub not loading please help me [here]("http://ubuntuforums.org/showthread.php?t=547318") (new thread)

---

