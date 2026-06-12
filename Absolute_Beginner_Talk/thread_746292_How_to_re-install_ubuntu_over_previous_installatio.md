---
title: "How to re-install ubuntu over previous installation?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by quddusaliquddus on 2008-04-05
Hi all :),
           I want to re-install ubuntu 7.10 and get rid of all of the previous installation of ubuntu. The last time i installed ubuntu was by following this guide:

**Installing Ubuntu 7.04 + Dual-Boot**
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

Do i have to partition the drive again? If not then do i follow these instructions as i did before? What about the space createed for the swap files? Do i have to create that again?

At the moment i have a dual boot up system with Vista and Ubuntu. I have previously partitioned C Drive to accomodate ubuntu and vista. 

any help is much appreciated.

Thanks! :D

Regards

Q

---

### Post by mikeyphi on 2008-04-05
Boot using the LiveCD
Choose Install
When the installer gets to suggesting Partitioning - select the Manual option

select your old ubuntu partition (it will be ext3) - select 'delete' then Apply

After the action is done go back to the same place and select the now free space as your (/) partition, mark it for formatting. No need to do anything about the Swap space - just leave it alone.

When you continue you should see that your choice was to format partition sdx(whatever it was before) and also to format the Swap partition - select OK and continue - install should continue OK

---

### Post by zvacet on 2008-04-05
Before you do anything it will be good to have separate home partition.If you don´t have it make it following [http://www.psychocats.net/ubuntu/separatehome]this]() guide.If you allready have it back up your data anyway.During installlation you will come to oartition step and then choose manual way.Selwect and delete old ubuntu partition and on that free space make fresh install.No need for new swap.

---

### Post by quddusaliquddus on 2008-04-05
thank u both very much for ur help! :D

---

