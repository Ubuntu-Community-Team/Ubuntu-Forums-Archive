---
title: "su password"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by proventech on 2006-01-03
isn't the password for su the same as the password for sudo?  :confused:

---

### Post by noob_Lance on 2006-01-03
it should be yes

---

### Post by proventech on 2006-01-03
:confused:  and if it doesn't work? :confused:

---

### Post by proventech on 2006-01-03
i figured it out.  had to set it with sudo passwd root

---

### Post by bored2k on 2006-01-03
The su passwd is hidden from you. Ubuntu uses sudo. If you want to enable the su  account, type ```
sudo passwd
``` and set it upt.

---

