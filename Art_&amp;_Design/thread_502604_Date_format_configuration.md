---
title: "Date format configuration"
date: 2007-07-16
forum: Art &amp; Design
---

### Post by WATAM on 2007-07-16
Date format configuration  dd/MM/aaaa not exist in ubuntu?
How to configure it?
Someone know?:confused:

---

### Post by WATAM on 2007-07-16
Date format configuration dd/MM/aaaa not exist in ubuntu?
How to configure it?
Someone know?

---

### Post by vnrat on 2007-07-16
# sudo gedit /etc/enviroiment

edit line

PATH=”/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games”
LANG=”en_US.UTF-8&#8243;

to

PATH=”/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games”
LANG=”en_GB.UTF-8&#8243;

restart -> and finish

---

