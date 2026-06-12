---
title: "[SOLVED] Autostart Evolution w/ Crontab"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by High Camp on 2008-03-14
Hi All

I'm trying to have Evolution start at 8am every morning. I have entered the following in my crontab file:
00 08 * * * evolution

For some reason it's not working.

Any help would be much appreciated, thanks.

---

### Post by Oldsoldier2003 on 2008-03-14
> **High Camp said:**
> Hi All

I'm trying to have Evolution start at 8am every morning. I have entered the following in my crontab file:
00 08 * * * evolution

For some reason it's not working.

Any help would be much appreciated, thanks.

evolution is a graphical app you need to start it with X...

---

### Post by Oldsoldier2003 on 2008-03-14
```
DISPLAY=:0. evolution
``` is what you need as the command, sorry i just realized i hadn't pasted that in :)

---

### Post by High Camp on 2008-03-15
Thanks very much. I thought that might be it but couldn't find any definite information.

I'll do the official "Thank This User" thing when I can find it. Right now I'm hung over and can't find the link to click.

Thanks,

EDIT: Like I said, I'm hung over, not sure how I missed the Thanks button.

---

