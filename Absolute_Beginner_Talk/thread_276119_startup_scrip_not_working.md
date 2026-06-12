---
title: "startup scrip not working"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by raul_ on 2006-10-12
this is a very stupid problem. i need to run : 
```

xset +fp /some/dir
xset fp rehash

```

so i tried adding this to the sessions menu in startup programs..it didn't work, so i thought "ok maybe this only works with programs" so i created a script 
```

#! /bin/bash
xset +fp /some/dir
xset rehash

```

and i tried putting that script on startup in the sessions menu, and in ~/.config/autostart/

but it didn't work. what am i doing wrong? ](*,)

---

### Post by oss_monkey on 2006-10-12
I don't know if you put it in the right place, but have you made the script executable?

> chmod +x startup_script_filename

---

### Post by raul_ on 2006-10-12
That's not the problem

EDIT: For some reason now it works. I created a new script, placed it in the autostart folder, and in addition i added it to my session manager. It's been workin for a while but only now i remembered to post

---

