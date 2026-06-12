---
title: "ifuse fails in Karamic"
date: 2009-11-03
forum: Apple Hardware Users
---

### Post by emil32 on 2009-11-03
Ifuse was working great in 9.04, but fails to load in 9.10. NB, the sources list was ## out in the upgrade, but even restoring it to the Karamic repos. didn't d/l all the dependencies e.g., libusb-1.0.3 

Thanks, Emil:(

---

### Post by drexell0680 on 2009-11-04
I'm having this problem too, back to mounting it as a camera - as it does before iFuse is installed.  Anyone having any luck with this?

---

### Post by quaff on 2009-11-05
i'm getting the same problem, i can't mount my iphone anymore after upgrading to karmic koala

---

### Post by mandreas on 2009-11-08
I'm also having the same problem. Any ideas?

---

### Post by BadSeqtor on 2009-11-09
Same problem here - iPhone will not mount after upgrade. Reinstall made no difference.

---

### Post by CanadianBac0n77 on 2009-12-12
i run the following command in Terminal:
```
 ifuse 
```then i get:
```
 ERROR: No mount point specified 
```

---

### Post by stefanb on 2009-12-26
try

```
sudo mkdir /media/iphone
sudo ifuse /media/iphone
```

---

### Post by jdj.1 on 2010-01-13
stefanb, your solution did the trick.  Thanks.

---

