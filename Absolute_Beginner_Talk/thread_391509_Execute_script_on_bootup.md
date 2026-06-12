---
title: "Execute script on bootup?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by meniscus on 2007-03-23
I want to run a particular script once everytime my computer boots up? Is this possible?

---

### Post by toddhd on 2007-03-23
I've been asking this same question for a while, and I think I just found some good info on what scripts activate when during boot time, and a built-in tool called BUM to help you manage them.

[http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)

---

### Post by djf_jeff on 2007-03-23
Sure it's possible. Just put the script in /etc/rc.local

This script is run at the end of every boot.

---

### Post by meniscus on 2007-03-23
Thanks for that link..


If i put the script in  /etc/rc.local will it run no matter whos logged on as user?

---

### Post by dreadlord_chris on 2007-03-23
> **meniscus said:**
> Thanks for that link..


If i put the script in  /etc/rc.local will it run no matter whos logged on as user?

yes...

---

### Post by meniscus on 2007-03-23
Thanks

---

### Post by djf_jeff on 2007-03-23
Just to give you more informations on this, this script is run _before_ any user log in. So, it doesn't matter if you log in with root/user or not at all.

---

