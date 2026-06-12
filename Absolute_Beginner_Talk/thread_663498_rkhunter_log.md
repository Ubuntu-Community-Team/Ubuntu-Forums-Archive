---
title: "rkhunter log"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-01-10
what does this mean?

```
[11:05:45] Info: Test 'hidden_procs' disabled at users request.
[11:05:45]
[11:05:45] Info: Test 'suspscan' disabled at users request.
```

---

### Post by bobyy on 2008-01-12
check .../etc/rkhunter.conf
you have this option:
DISABLE_TESTS="suspscan hidden_procs deleted_files packet_cap_apps"
# Please do not enable by default as suspscan is CPU and I/O intensive and prone to
# Also be aware that running suspscan in combination with verbose logging on,
 maybee i am whrong..

---

### Post by someoneouthere on 2008-01-12
> **bobyy said:**
> check .../etc/rkhunter.conf
you have this option:
DISABLE_TESTS="suspscan hidden_procs deleted_files packet_cap_apps"
# Please do not enable by default as suspscan is CPU and I/O intensive and prone to
# Also be aware that running suspscan in combination with verbose logging on,
 maybee i am whrong..

superscan i suppose does a more detailed intensive search/check?

---

### Post by bobyy on 2008-01-12
yes....and use this database..

$cat /var/lib/rkhunter/db/suspscan.dat

..i respond you to the thread with internet logs....

---

