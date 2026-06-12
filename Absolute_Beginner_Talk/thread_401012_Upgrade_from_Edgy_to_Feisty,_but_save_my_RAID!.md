---
title: "Upgrade from Edgy to Feisty, but save my RAID!"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by webjames on 2007-04-04
Hi Ubuntuers,
Your help would be invaluable to me during the process of upgrading my system from edgy to feisty. This is my proposed upgrade:

I currently have Edgy with a software raid5 array, mdadm. mounted as the /home area.

I would like to have the same setup but with feisty. i have only really just got used to edgy and i've been using it a few months, and as i have been messing it around a bit i want a clean start with feisty.

i am proposing to do a fresh install and during the install find the raid and the /home partition and remount it as home, then input the same user. is this sensible? how would i go about doing this, i have lots of valuable data on the raid 5 array hence raid5 in the first place. i don't want the installer to overwrite anything.

has anyone tried something similar?

Thank you,

James :)

---

### Post by Kobalt on 2007-04-04
Using a separate disk/partition for your /home is actually a very good idea, it's the safest way not to lose any data during an upgrade or a reinstall. You will be able to select your existing /home partition from the Feisty installer and if you specify it not to format that disk (it's just a click away) then your data won't be touched. 
And if you chose the same username/password you really shouldn't have any problems. You'll keep your emails, your Firefox bookmarks, etc. : everything that's in your /home.

---

### Post by Maestro23 on 2007-04-04
When you get ready: [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

---

