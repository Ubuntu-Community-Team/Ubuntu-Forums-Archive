---
title: "Boot from USB install on iMac OR PC"
date: 2010-10-30
forum: Apple Hardware Users
---

### Post by try2hard on 2010-10-30
Hello everyone. I want to install Ubuntu (planning on 10.10) on to a USB flash drive or external hard drive. I understand it can wear a flash drive faster than normal so I may just opt for using my external USB hard drive.

I would like to install the system so that I can boot it on my iMac (Intel) OR a PC, if that is possible. During my "trial installation", when I was doing manual partitioning, I was unsure if I had to do anything special to make this possible. I am aware of the challenges of booting from USB on an iMac but I am happy to use either a Ubuntu Boot CD or a Boot Manager such as pLOP. I already use the pLOP CD on the iMac to boot into a Live USB distro.

My plan is to partition my external drive as follows:

sdb1: /boot (How big should this be? 100MB?) Which is the best format? Ext2?
sdb2: / (root) as ext3 or ext4
sdb3: /swap (10% of root?) ext2 or ext3

Is anything above incorrect? Will it be possible to do what I want to do? Will this make the system bootable on either my iMac (using boot CD) and a x86 PC?

Thank you for your help. I look forward to my Ubuntu installation.

---

### Post by try2hard on 2010-10-31
Anyone have any ideas?

---

