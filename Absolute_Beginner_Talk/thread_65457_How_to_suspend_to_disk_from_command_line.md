---
title: "How to suspend to disk from command line?"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by bamanzi on 2005-09-14
Yes, I can 'hibernate' (suspend to disk) my ubuntu by using the logout menu.

but how can I do the same job from the command line? :?

---

### Post by heimo on 2005-09-14
This should do it:
```
sudo sh -c "echo 4 > /proc/acpi/sleep" 
```

---

