---
title: "CD/DVD doesn't mount anymore when upgraded to Feisty"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by vnt87 on 2007-04-27
It just came to my attention that my 2 DVD drives don't work anymore after I upgraded to Feisty a couple of days ago. 
I mostly use USBs nowadays so I didn't know about right away. But today, I tried to insert some CDs and DVDs into them and neither showed me anything anymore. It wasn't like this back in Edgy. 
Can anybody point me to a solution to amend this please, much appreciate it.

PS. just to add that when I tried to manually mount them, it says something abou 'special device dev/hd*x (where x is my DVD drives letter)* is not available

---

### Post by ajmorris on 2007-04-27
> **vnt87 said:**
> It just came to my attention that my 2 DVD drives don't work anymore after I upgraded to Feisty a couple of days ago. 
I mostly use USBs nowadays so I didn't know about right away. But today, I tried to insert some CDs and DVDs into them and neither showed me anything anymore. It wasn't like this back in Edgy. 
Can anybody point me to a solution to amend this please, much appreciate it.

PS. just to add that when I tried to manually mount them, it says something abou 'special device dev/hd*x (where x is my DVD drives letter)* is not available

try sudo mount /dev/cdrom

---

### Post by sharm on 2007-04-28
> **ajmorris said:**
> try sudo mount /dev/cdrom

Still broken for me.  These are CDs I burned myself some time ago, but they worked fine on Dapper and Edgy (and still work in Mac OS X, etc).

sandy@tortilla:~$ sudo mount /dev/cdrom
Password:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

sandy@tortilla:~$ dmesg | tail
[   64.163275] Bluetooth: L2CAP socket layer initialized
[   64.377383] Bluetooth: RFCOMM socket layer initialized
[   64.377403] Bluetooth: RFCOMM TTY layer initialized
[   64.377407] Bluetooth: RFCOMM ver 1.8
[   75.911726] eth0: no IPv6 routers present
[ 8196.926429] process `beagled-helper' is using deprecated sysctl (syscall) net.ipv6.neigh.default.base_reachable_time; Use net.ipv6.neigh.default.base_reachable_time_ms instead.
[16046.530816] Unable to identify CD-ROM format.
[16103.094165] Unable to identify CD-ROM format.
[16207.019136] Unable to identify CD-ROM format.
[16373.529537] Unable to identify CD-ROM format.

---

### Post by sharm on 2007-04-28
This launchpad bug seems to be related:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119)

---

### Post by vnt87 on 2007-04-30
So is there a solution?
I found that my burning softwares (K3b and Nero3 beta) are still recognizing the drives and the discs inside them. But Ubuntu (or is it Nautilus fault?) is not.

---

### Post by zvacet on 2007-04-30
Did you try to go to **system>settings>removable drives and media** and chek boxes there

---

### Post by vnt87 on 2007-05-01
> **zvacet said:**
> Did you try to go to **system>settings>removable drives and media** and chek boxes there

I went there but I'm not sure which boxes should be checked and which ones shouldn't be.
Anyway, I left my disc in the drive when I reboot the computer and surprisingly, it's here. However I get a lot of the "I/O error" fault when trying to copy from the disc. This error often shows up when encountering corrupted media, but I don't think this is the case since I can copy these files just fine under Windows.

---

### Post by gregdwih on 2007-05-02
sudo mount /dev/cdrom works but have to restart, not just restart X but reboot.:)

---

