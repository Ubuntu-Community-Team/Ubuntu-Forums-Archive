---
title: "/Windows folder under root using up available space"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Rinulin on 2006-09-11
I installed Ubuntu 6.06 in July and, following the instructions at [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) I then mounted my ntfs partition so that I could have read access to my Windows files.

Recently, I downloaded Baobab to get an idea of how my Ubuntu partition is doing on available space. I have 30+ gigs partioned for Ubuntu, and after running Baobab, I see that I have a /Windows folder under root that is (according to Baobab) using about 27 gb of my available space. The Windows folder actually contains everything that I have on my C: drive when I boot into Windows.

My question is, do I have duplicate data on both partitions? I'm concerned about my Ubuntu partition filling up, and used Baobab to try and determine what I need to delete. I remembered that I had mounted my Windows partition and thought that I would simply unmount that drive. However, when I type ```
sudo fdisk -l
``` I don't see my ntfs partition listed.

---

### Post by Jussi Kukkonen on 2006-09-11
I've never heard of baobab, so can't help there. 

The part about fdisk not seeing partitions that you have actually mounted, sounds a little scary. Are you sure this is what happens?

Try with plain ordinary *df -h* on the command line, it'll show mounted filesystems and their disk usage.

---

### Post by Rinulin on 2006-09-11
Using the df -h, this is what I get:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             22G   12G  9.5G  55% /
varrun                506M  128K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  108K  506M   1% /dev
devshm               506M     0  506M   0% /dev/shm
lrm                    506M   18M  488M   4% /lib/modules/2.6.15-26-k7/volatile
/dev/sda1             51G   28G   24G  54% /windows

```

Is /dev/sda1 part of my Ubuntu partition? It doesn't really make sense because I don't believe that I allocated 51G to Ubuntu.

---

### Post by Midway on 2006-09-11
"/Windows folder under root" looks very familiar to me.  I went through this when I installed 6.06 early last month.  During the install it asked me for the mount point for Windows which confused me since no other distro has asked me that before so I typed in "/Windows". Look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=229821]("http://www.ubuntuforums.org/showthread.php?t=229821")

Maybe it will help you. :)

---

### Post by Jussi Kukkonen on 2006-09-12
> Is /dev/sda1 part of my Ubuntu partition? It doesn't really make sense because I don't believe that I allocated 51G to Ubuntu.

No. /dev/sda1 is just a partition that happens to be mounted at the moment. If you followed the instructions you linked to, /windows is your NTFS mount point, so */dev/sda1* is your NTFS partition. */dev/sda2* is your linux partition. You have used a little over half of the 22GB allocated for the linux partition.

---

