---
title: "Disk poweroff"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by calelettus on 2008-01-27
Two questions really:

1) I can't seem to find a way to poweroff my disk after a period of time. Is there an  ACPI equivalent in Ubuntu or another way to put the disk to sleep and have it resume upon striking a key?

2) I read several months ago of a problem where Ubuntu was improperly handling disk shut down during poweroff (for laptops I believe). Is that still the case or was it ever? Resolution?

Thanks!

---

### Post by jw5801 on 2008-01-27
I dunno about the first question, But the second issue has been resolved. One incarnation of the Linux kernel was not properly parking the drive on shutdown, forcing the HDD to use the emergency head park (like when you hard reboot). The issue was present in the 2.6.17 kernel (Edgy), a patch was introduced to the 2.6.20 kernel (Feisty) and the bug was completely resolved by the 2.6.22 kernel (Gutsy).

---

### Post by Majorix on 2008-01-27
For the first Q, I am not on Gnome Ubuntu right now so I can't confirm, but you should be able to set the preferences in System > Prefs (or Admin, check both) > Power Management.

---

### Post by Casual Fan on 2008-01-27
See the comment from naom in this thread:

[http://ubuntuforums.org/showthread.php?t=404977&highlight=shutdown+noise&page=2](http://ubuntuforums.org/showthread.php?t=404977&highlight=shutdown+noise&page=2)

I was getting a brief whining noise from the HD when my laptop shut down in Feisty...naom's fix stopped it.

---

