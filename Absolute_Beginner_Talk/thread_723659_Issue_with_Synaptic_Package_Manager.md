---
title: "Issue with Synaptic Package Manager"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by CloudFX on 2008-03-13
When I try to run Synaptic Package Manager, it gives me this output:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

When I run **dpkg --configure -a**, I get the output 

```
dpkg: requested operation requires superuser privilege
```

I'm the admin of this computer, and also the only account. What needs to be done?

---

### Post by NightwishFan on 2008-03-13
```
sudo dpkg --configure -a
```
Then type your password.

---

### Post by CloudFX on 2008-03-13
Great! it worked... who knew it would be that easy.

Thanks much man.

---

