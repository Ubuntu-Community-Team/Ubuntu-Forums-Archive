---
title: "Secondary HDD"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by prasad_bhatla on 2007-04-17
Hi

About a week back got Ubuntu6.10 running with practically no hangups including Internet connection and wireless connectivity.

I had to dump an old PC , but retrieved the 8,4Gb HDD which I have added as /dev/hdb and partitioned as below.

prasad@prasad-desktop:~$ sudo fdisk -l /dev/hdb

Disk /dev/hdb: 8622 MB, 8622931968 bytes
255 heads, 63 sectors/track, 1048 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         765     6144831   83  Linux
/dev/hdb2             766        1048     2273197+  82  Linux swap / Solaris

I deleted the old swap partition and managed to get the  new swap partition into action by editing the /etc/fstab. ( Thats another story !!) and  using command mkswap.
Cannot  say if this is the right way  to do it. All I can say it works !!

I want to use the /dev/hdb1 for the /home directory .
Where do I make the changes ? /etc/fstab ?  Would this be the only place ??

Cheers

---

### Post by rmemm on 2007-04-17
/etc/fstab is the place as far as I know.  See man fstab for the format or just ad another line like what's there.

Rob

---

### Post by confused57 on 2007-04-17
See this guide for making a separate home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Marsolin on 2007-04-17
I'm not sure the step-by-step for Ubuntu, but in Kubuntu the mounting can be done through the Disk & Filesystem app on the Advanced tab of System Settings. No manual editing of fstab is necessary.

In my opinion, creating a separate partition for /home is a great way to go. It really comes in handy if you ever need to reinstall a new OS, just reformat the / partition,tell it to use the other existing partition for /home, and install a clean OS while still keeping all of your data and individual settings.

---

