---
title: "[SOLVED] Where are the downloaded packages kept"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by guguma on 2007-08-12
Hello,

I mistakenly downloaded some kde packages and want to erase them. Where are they downloaded?

---

### Post by mikewhatever on 2007-08-12
Check you home directory, or, perhaps /var/cache/apt/archives. In the latter case, use the following command:
> sudo apt-get clean

---

### Post by qamelian on 2007-08-12
Packages installed via the package managers are archived at ```
/var/cache/apt/archives
```

---

