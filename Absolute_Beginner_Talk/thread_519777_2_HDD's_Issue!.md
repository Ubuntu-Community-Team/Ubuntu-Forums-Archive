---
title: "2 HDD's Issue!"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-08-07
Here is the run down:
1. I installed ubuntu on my laptops  HDD
2. I then pluged an externl HDD into laptop, booted up the ubuntu live cd, and installed ubuntu on the external hdd
3. now, neither hdd will boot without the other
HEEEEEEEEEEEEEEELLLLLLLLLLLPPPPPPPPPPPPPPPPPPP!!!!!!!!!
Can i edit grub (and if so how) to work without the other hdd, its grub by the way that wont allow the hdd to boot.

---

### Post by psusi on 2007-08-07
Use the cd to boot from the hard disk, then run grub-install to reinstall grub.

---

### Post by ron999 on 2007-08-07
Just as psusi says above.
There's instructions in the thread here:-[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by kevin11951 on 2007-08-07
thanks, all i did was boot into the regular hdd and type 'sudo grub-install /dev/sda' and everything was better! thanx again!

---

