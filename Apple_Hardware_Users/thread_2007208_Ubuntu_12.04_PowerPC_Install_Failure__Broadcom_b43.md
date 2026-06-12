---
title: "Ubuntu 12.04 PowerPC Install Failure / Broadcom b43-phy0 error"
date: 2012-06-20
forum: Apple Hardware Users
---

### Post by rearviewmirror on 2012-06-20
I can't get past the initial start up screen when installing 12.04 on a PowerPC Mac Mini.  There is a kernel panic comes up with an error related to "b43-phy0 error".  

I get the Broadcom needs a driver, installing 10.04 reminds me of this after it's installed.  When install 12.04 it doesn't make it past the initial setup screen.

Any thoughts?

---

### Post by Iolo34 on 2012-06-21
According to the PowerPC Ubuntu FAQ, some broadcom wireless cards / chips can cause hangs in the boot process. The workaround is to pass 
b43.wireless=blacklist as a yaboot parameter.

---

