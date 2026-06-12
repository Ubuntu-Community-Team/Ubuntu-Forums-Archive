---
title: "how to upgrade to fesity fawn"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2007-05-20
i've been using ubuntu 6.04 LTS for about 6 months now and i love it. i now want to upgrade to fesity fawn. what's the easiest way to go about this? (please note i have a dual boot set up for XP). during the installation process, should i just tell ubuntu to intall all files to this partition, or should i reformat and then install feisty here? 


i have already backed up my home dir, sources.list, fstab, xorg.conf, ssh server config, ftp server config. any other files i should back up on my external hdd?


thanks.

---

### Post by HereInOz on 2007-05-20
Firstly, open a terminal and type:

gksu "update-manager -c"

This will prepare your Dapper install for an upgrade to Edgy - you will now see the statement at the top of the upgrade manager that an upgrade is available.

Once upgraded to Edgy, you can then upgrade to Feisty.

Other than that, you could do a full re-install, and provided you used manual partitioning, and told the partitioner to leave your Windows partition(s) alone, you should have a a brand new Feisty, dual boot with Windows.

---

### Post by rsambuca on 2007-05-20
If you have your sensitive data files backed up, I would just install Feisty overtop of your old Dapper partition.  You are likely to have less potential problems with a completely fresh install as opposed to a double upgrade.

---

