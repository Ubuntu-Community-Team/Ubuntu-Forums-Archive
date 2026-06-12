---
title: "have to uninstall ubuntu desk and install server ed."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by texplorer on 2007-07-31
The reason I ask this is that the HD space is limited. Server ed. is more suited to my project. 

I have two unrecognized partition under XP's computer management (disk management), see pic. I though Ubuntu should have one partition only. The moment I installed Ubuntu Desktop, I guess I partitioned my HD twice. Should I reclaim one of the two partitions? 

I am trying minimize the impact to the PC (backups, reinstall XP etc.) and make the after result as clean as possible. 

Would there be a possible solution? I am still a newbie to Linux, detailed commands/other tutorial  for the process would be greatful.

Thanks, 

BTW, am I allowed to use the server ed. for commercial purpose later?

---

### Post by p_quarles on 2007-07-31
The smaller unknown partition is your swap partition. It's a logical partition (according to your screenshot), so formatting the primary Ubuntu partition will get rid of it and create its own swap.

---

