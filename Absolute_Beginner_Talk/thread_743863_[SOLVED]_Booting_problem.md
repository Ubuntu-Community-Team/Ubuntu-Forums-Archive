---
title: "[SOLVED] Booting problem"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Fred_E _krugar on 2008-04-03
When I boot I get this message fsck.ext3: Unable to resolve 'UUID=89cd17ed-ddbb-4fb3-907e-edb63784883f'

Then I have to type reboot then everything loads fine. I can live with this but is there a way I can get rid of this? I have to go through this every time I boot up.

---

### Post by forestpixie on 2008-04-03
You need to edit one of the fstab lines I would think - have you done any partition work?

Use ```
sudo blkid
``` to get UUID for your partitions edit fstab ```
gksudo gedit /etc/fstab
``` and find the line that has > 89cd17ed-ddbb-4fb3-907e-edb63784883f in it and change to the value you get from blkid for that partition.

---

