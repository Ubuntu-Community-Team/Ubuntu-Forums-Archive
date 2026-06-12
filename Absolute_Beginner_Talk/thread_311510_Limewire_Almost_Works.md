---
title: "Limewire Almost Works"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-12-03
I almost got Limwire to work.  I downloaded the RPM, it's sitting on my desktop.  LimeWireLinux.RPM.  This is the problem: 

wesley@laptop:~$ fakeroot alien -d LimeWireLinux.rpm
File "LimeWireLinux.rpm" not found.

Why doesn't it see it?  I downloaded fakeroot alien, so that isn't the problem.

---

### Post by taurus on 2006-12-03
Maybe because you downloaded it to ~/Desktop!!!

```
cd ~/Desktop
fakeroot alien -d LimeWireLinux.rpm
```

---

### Post by OptimusPrime on 2006-12-03
Thank you, good sir.

---

