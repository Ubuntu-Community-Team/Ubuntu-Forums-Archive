---
title: "Trackpad tap functionality"
date: 2007-01-09
forum: Apple PPC Users
---

### Post by b5mC on 2007-01-09
For starters, Ive had 6.06 installed for a while now however, it wasnt until a day ago I found out that--- ```
sudo trackpad tap
``` enables tapping functionality.  Ive been using an iBook G3 without tapping for a while until a came across the answer in the forums.  

The problem:  How do I maintain---```
sudo trackpad tap
``` setting after hibernation or a system restart?  Its not really a big deal I would just like to figure out how to resolve this.

Thanks

---

### Post by ssam on 2007-01-09
try putting a script in

```
/etc/acpi/resume.d
```

it probably does not need the sudo when it is there, as those scripts will be run as root.

update:
actually i think the right place might be

```
/etc/apm/resume.d
```

---

### Post by b5mC on 2007-01-09
How exactly would I accomplish this?  And also are all scripts located in this directory started automatically?

---

### Post by ajmctaggart on 2007-07-17
Has anyone ever figured this out?

---

