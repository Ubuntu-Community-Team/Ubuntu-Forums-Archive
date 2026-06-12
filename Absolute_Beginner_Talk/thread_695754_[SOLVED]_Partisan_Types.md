---
title: "[SOLVED] Partisan Types"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Yuki_Nagato on 2008-02-13
I am currently attempting to dual boot OpenSUSE and Ubuntu 7.10.

Recommendations on a partisan setup for a 40 Gig hard drive?

Can Ubuntu and OpenSUSE share the same "/home" partisan?

---

### Post by Ek0nomik on 2008-02-13
> **Yuki_Nagato said:**
> I am currently attempting to dual boot OpenSUSE and Ubuntu 7.10.

Recommendations on a partisan setup for a 40 Gig hard drive?

Can Ubuntu and OpenSUSE share the same "/home" partisan?

It's called partition.  Just an fyi.

Anyways, each person will have a different suggestion.  You are correct though that Ubuntu and OpenSuse can share the same home partition.  This is a good idea because then you don't waste extra space with having the same software installed in both distributions.  You could setup some space for a /home partition, and then have two additional ext3 partitions for the root file systems of Ubuntu and OpenSuse.

---

### Post by Paqman on 2008-02-13
A pretty standard setup would be:

Ext3 Partition 10GB for Ubuntu /
Ext3 Partition 10GB for OpenSuse /
Ext3 Partition 19GB for /home
Swap partition 1GB

Swap needs to be 1-1.5x the size of RAM on a laptop, or a desktop with under 1GB RAM. With 1GB or more of RAM on a desktop I wouldn't bother having a swap larger than 1GB (as you'll probably never touch it anyway)

This setup assumes you're using /home as shared storage. If you needed more room you could quite safely shave a couple of GB off each / partition.

---

### Post by Yuki_Nagato on 2008-02-15
Thank you for enlightening me with the proper terminology.  And thank you for the recommendation on partition setup.

---

