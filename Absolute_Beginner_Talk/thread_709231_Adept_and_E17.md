---
title: "Adept and E17"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by james09173 on 2008-02-27
I just got Enlightenment (E17) working on my Kubuntu (Gutsy). Every time I try and open the Adept Package Manager I get the following error messages:

Will not save configuration.
Configuration file "/home/james/.kde/share/config/adept_installerrc" not writable.
Please contact your system administrator.

I hit OK and then get

This application needs special administrator (root) privileges. Please run it as root or through kdesu or sudo programs

I've tried things like "sudo adept" in the Konsole but that didn't work. Any ideas?

Thanks in advance!

---

### Post by SOULRiDER on 2008-02-27
Try running it with
```
kdesu adept-manager
```

Alternatively you could use Aptitude, its command line but its still quite friendly. run it by doing
```
sudo aptitude
```

---

### Post by james09173 on 2008-02-27
Thanks! The "sudo aptitude" line worked. No luck with the kdesu command.

---

### Post by p_quarles on 2008-02-27
> **james09173 said:**
> Thanks! The "sudo aptitude" line worked. No luck with the kdesu command.
You may need to install that if you don't already have kde-core:
```
sudo aptitude install kdesudo
```

---

