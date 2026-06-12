---
title: "/dev/dvd in Gutsy"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-10-20
Are DVDs located in /dev/dvd in Gutsy? My DVD would be located there for Fiesty(when I had it), but now when I load it (with /dev/dvd as preference) nothing appears. Is it a different path now in Gutsy? If so, what? Thank you.

EDIT: When I run this program and hit load after I insert the DVD it says "/dev/dvd" doesn't exist. How can I get this problem resolved.

---

### Post by Pumalite on 2007-10-20
Does your DVD work?. If yes, then you should find a device in /dev

---

### Post by CapitanYochua on 2007-10-22
Bump. I added some info in the original post, and changed the title to be more precise.

---

### Post by Maestro23 on 2007-10-22
> **CapitanYochua said:**
> Bump. I added some info in the original post, and changed the title to be more precise.

Look at your** /etc/fstab**

Should tell you what you need to know.

---

### Post by Pumalite on 2007-10-22
Is best when DVD drive is 2nd Master and set to 'Auto' in BIOS.

---

### Post by CapitanYochua on 2007-10-22
> **Pumalite said:**
> Is best when DVD drive is 2nd Master and set to 'Auto' in BIOS.

It is.

 Now, what do I do with /etc/fstab?

---

