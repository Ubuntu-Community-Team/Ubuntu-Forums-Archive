---
title: "Helppppp!!!!"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by thekylehome@gmail.com on 2008-02-19
Hello everyone!

I have a very big pain on my hands! Every time I start my computer, I have to go into the restricted drivers window, uncheck the box under my Broadcom 43xx, and let it unstall the driver. Then, I have to recheck the box and then it reinstalls the firmware/driver. Are there any possible solutions to this?
Thanks!

---

### Post by myddewji13 on 2008-02-19
use ndiswrapper

---

### Post by thekylehome@gmail.com on 2008-02-19
yes, I have tried that! infact I have ndiswrapper utils installed now... but same problem...

---

### Post by thekylehome@gmail.com on 2008-02-19
Anyone have any ideas?????

---

### Post by bodhi.zazen on 2008-02-19
Try starting a thread with a more appropriate title.

> Helppppp!!!!

Who wants to click on that title to see what it is about ???

See this link.

[http://ubuntuforums.org/showthread.php?t=700739](http://ubuntuforums.org/showthread.php?t=700739)

---

### Post by lncoll on 2008-02-19
You can disable the restricted driver, edit /etc/default/linux-restricted-modules-common and add :

```
DISABLED_MODULES="43xx"
```

Then install ndiswrapper.

---

