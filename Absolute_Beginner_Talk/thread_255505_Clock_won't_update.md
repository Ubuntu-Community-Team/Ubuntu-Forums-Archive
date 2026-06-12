---
title: "Clock won't update"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-09-11
I have set the servers to use and told it to update...it gives me the correct time, BUT the actual desktop clock refuses to change!!  GRRRR

Any solutions?

Thanks

---

### Post by bulldog on 2006-09-11
Right click the dam*** thing and do it manually.:-\"

---

### Post by morequarky on 2006-09-11
Let me explain more.

1. I right click on the THING.
2. I set the time.
3. I set the server.
4. I tell it to update.
5. The time it SHOWS IS CORRECT.
6. I click OK.
7. The desktop clock does NOT CHANGE!!!!!!!!!!!!!!!!

GOT IT??

---

### Post by jordanmthomas on 2006-09-11
Does logging out and then back in do anything for you or is the clock still wrong?
Also, how wrong is it?  Is it off by x hours and 0 minutes?

---

### Post by bodhi.zazen on 2006-09-11
I feel your pain. Took me a while to figure this out myself.

Not sure if the problem is with you timezone (tzconfig) or time server (ntp).

I know you are frustrated, but I need more information.

Do you have ntp installed?

In a terminal, try:
```
sudo tzconfig -> follow on screen instructions to set your timezone.

sudo ntpdate ntp.nasa.gov
```

Did that fix?

Now start ntpd.

---

