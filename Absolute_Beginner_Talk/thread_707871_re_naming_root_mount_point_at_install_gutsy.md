---
title: "re: naming /root mount point at install gutsy"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by fallsoff on 2008-02-25
Hi all,
I did an Ubuntu install from a Format Linux magazine coverdisk. It went south due to weird addons that I couldnt work around_<xcfe4>, I think.  It took over the desktop and I couldn't wiggle around it or uninstall, so I bailed.

Now I am using straight Canonical Gutsy. I formatted /root in XP to eliminate the previous install. Now the Ubuntu installer keeps telling me that I have to name or mount the /root partition. I am at that point in the reinstall,and it wont accept using </root>, so I am stuck. I have a 1 G linux swap partition and 9G to use as /root. I am not allowed to use /root even though that worked last time.
Can anyone help me out? I am stuck!
Thanks,
fallsoff

---

### Post by Austin_KW on 2008-02-25
Use the advanced/manual option, select your 9G partition and mount "/" not "/root" on it, with an etx3 file system. 
/root is the root user's home directory, / is the root of the linux file system. 
Also click the box to format this root partition.

---

