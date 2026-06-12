---
title: "/etc/cron.daily/ntupdate with run-parts"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by mat087 on 2007-10-09
Hi everybody!

Here is my problem


When I run **sudo run-parts /etc/cron.daily/**. I've got the following ouput : 

```
run-parts: failed to exec .//ntupdate: Exec format error
run-parts: .//ntupdate exited with return code 1
```

When I run **sudo /etc/cron.daily/ntupdate**. I've got the following output : 

```
9 Oct 12:12:31 ntpdate[10023]: adjust time server 91.189.94.145 offset -0.000222 sec
```

Here is the content of **/etc/cron.daily/ntupdate** :

```
ntpdate ntp.ubuntu.com
```


Do you know why does **/etc/cron.daily/ntupdate** fail when it is executed by run-parts ?

Thanks,
Mathieu

---

### Post by milosz.galazka on 2007-10-09
Try
```

#!/bin/sh
ntpdate ntp.ubuntu.com
```

---

### Post by mat087 on 2007-10-09
Thanks milosz.galazka. It works!

---

