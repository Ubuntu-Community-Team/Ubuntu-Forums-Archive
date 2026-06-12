---
title: "Is there a command to show the member(s) of a group?"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-02-13
'groups username' shows the group(s) the user belongs to. Is there a command to show the member(s) of a group?

Thanks !

---

### Post by heimo on 2006-02-13
[quote=Akhran]'groups username' shows the group(s) the user belongs to. Is there a command to show the member(s) of a group?

Thanks ![/quote] 
I don't know. :rolleyes: I always just "less /etc/group", but if you want something more complex ;) this should list users in www-data group:

```
grep ^www-data: /etc/group | cut -d: -f4
``` (someone else will give better answer)

---

