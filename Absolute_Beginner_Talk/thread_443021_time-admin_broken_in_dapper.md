---
title: "time-admin broken in dapper?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by popkid on 2007-05-14
Hi,

Hadn't noticed before, but my computer's time display is one hour slow....

I tried using the change time option from the admin drop down and just got the message "time-admin has quit unexpectedly"

entering sudo time-admin at the console returns the following:


[PHP]** (time-admin:5247): WARNING **: Could not open */usr/share/zoneinfo/zone.tab*


** ERROR **: Unable to load system timezone database.
aborting...[/PHP]

further investigation revelas that there is no zone.tab file?

Any ideas?

Thanks, 

pK ;)

---

### Post by popkid on 2007-05-17
Just an update to report the fix to this problem if anyone is interested!

I created a new empty zone.tab file by issuing the command

sudo touch /usr/share/zoneinfo/zone.tab

this allowed time-admin to start, but still couldn't change timezone as there were none listed and time-admin would fall over with the "quit unexpectedly" message again...

since there were no timezones listed at all, I re-installed the "locales" package through synaptic, and lo and behold I now have a clock that tells the right time and time-admin works properly

pK ;)

---

