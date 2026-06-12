---
title: "Apache"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by rodin69 on 2007-11-25
Hi,

I've been trying to uninstall Apache from my ubuntu machine but have failed so far. What's the way to do it  ? Thanks in advanced.

Rodin

---

### Post by Taboo Mirage on 2007-11-25
The question would be: how did you *install* it?  That would indicate how you'd go about removing it.

If you installed it from the repositories:

```
sudo aptitude remove apache2
```

And to completely remove it, including configurations:

```
sudo aptitude --purge remove apache2
```

---

### Post by rodin69 on 2007-11-25
Thanks a million. 

Rodin

---

