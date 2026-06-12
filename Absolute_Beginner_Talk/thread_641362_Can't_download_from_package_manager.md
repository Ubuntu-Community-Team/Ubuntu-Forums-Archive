---
title: "Can't download from package manager"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by jpsimm on 2007-12-15
I just upgraded from 6.06 to 7.10 (clean new install) and notice that I cannot download additional apps or anything else from the online package library either through the "manager" or through the "add/remove" menu.

When I select something, I wanted Thunderbird Mail, very quickly a screen comes up telling me to refresh.   I do this and two more screens go by so fast I can't read them then I am returned to the manager screen.   This happens when I try to "select" an item.   I thought this to be a bug but I see no one else crabbing about it and I am told that my computer is up to date by the update manager.

If no one can help me I think I'll go back to 6.06 that was flawless.

Thanks

---

### Post by overdrank on 2007-12-15
> **jpsimm said:**
> I just upgraded from 6.06 to 7.10 (clean new install) and notice that I cannot download additional apps or anything else from the online package library either through the "manager" or through the "add/remove" menu.

When I select something, I wanted Thunderbird Mail, very quickly a screen comes up telling me to refresh.   I do this and two more screens go by so fast I can't read them then I am returned to the manager screen.   This happens when I try to "select" an item.   I thought this to be a bug I see no one else crabbing about it and I am told that my computer is up to date by the update manager.

If no one can help me I think I'll go back to 6.06 that was flawless.

Thanks

Hi and I would suggest checking your repos and making sure they not commented out.
```
gksudo gedit /etc/apt/sources.list
```

---

