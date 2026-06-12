---
title: "no slackware on vmware"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-07-13
when i tried to install slackware on vmware it first asked me to create the target drive for installation.
but when i used "cfdisk"
i obtained following output

 > FATAL ERROR: Cannot open disk drive
                          Press any key to exit cfdisk




any suggestions.
NB: i got same output when i used cfdisk on XUBUNTU

---

### Post by Kilz on 2006-07-13
> **wolfmaniac said:**
> when i tried to install slackware on vmware it first asked me to create the target drive for installation.
but when i used "cfdisk"
i obtained following output

 



any suggestions.
NB: i got same output when i used cfdisk on XUBUNTU

vmware creates virtual disk drives in the /home/<username>/vmware/<virtual machine name> folder. They are not partitions on the physical disk drive. The cfdisk command to look for them may only work when running the virtual machine in vmware.

---

