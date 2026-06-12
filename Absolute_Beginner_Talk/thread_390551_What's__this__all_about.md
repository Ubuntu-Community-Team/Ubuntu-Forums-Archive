---
title: "What's  this  all about?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-03-22
I was going through my File System and at /var/run I came across 2 folders (sudo and  cluster) and 
1 file (crond.reboot) that had red X's in front of them.  What's that all about and should I  do something?  Thanks

---

### Post by mcduck on 2007-03-22
> **jtx472 said:**
> I was going through my File System and at /var/run I came across 2 folders (sudo and  cluster) and 
1 file (crond.reboot) that had red X's in front of them.  What's that all about and should I  do something?  Thanks

Those files are owned by root, and contain information that normal users should not be able to read. So that's why you see red crosses on them when viewing as normal users. No reason to do anything about it :)

---

### Post by scxtt on 2007-03-22
my crond.reboot has a "lock" when i use konqueror to look in /var/run ... it doesn't have any permissions "----------" ... i wouldn't change it, esp. if you were just perusing / ...

---

### Post by jtx472 on 2007-03-22
Thanks much.

---

