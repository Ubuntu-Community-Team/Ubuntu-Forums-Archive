---
title: "shutting down azureus from the command line?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by p.i.m.p on 2006-08-27
can somebody tell me how to shut down azureus from the command line as i want to put it down in my cron file.. thanks in advance!

EDIT - i found the solution.. azureus --closedown shuts down any running instances of the program :)

---

### Post by TFX360 on 2006-08-27
> **p.i.m.p said:**
> can somebody tell me how to shut down azureus from the command line as i want to put it down in my cron file.. thanks in advance!

EDIT - i found the solution.. azureus --closedown shuts down any running instances of the program :)

And if that doesn't work you can always use:

```
killall applicationname
```

You can find the application name by:

```
ps -ef | grep applicationname
```


Kind regards,


TFX

---

