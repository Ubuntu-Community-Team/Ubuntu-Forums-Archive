---
title: "Problem running cron"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by kadymae on 2006-04-05
It dawned on me that I've never run cron on this laptop.

And, since there's no "mac janitor"esque interface I can find, I went to ye olde command line and typed:

sudo cron -f

I'm getting this error message:
cron: can't lock /var/run/crond.pid, otherpid may be 4336: Resource temporarily unavailable

---

HUH?!

---

Your assistance is appreciated.

---

### Post by htinn on 2006-04-05
Probably because cron is already running in the background. About the only thing I know about cron is what I read here:

[http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)

---

### Post by dcstar on 2006-04-06
Plain old cron on any machine that is not running 24/7 isn't that useful, look at installing the anacron package.

---

### Post by kadymae on 2006-04-06
[QUOTE=dcstar]Plain old cron on any machine that is not running 24/7 isn't that useful, look at installing the anacron package.[/QUOTE]
Thanks David,

I presume anacron is something I can get w/synaptic?

---

### Post by dcstar on 2006-04-06
[QUOTE=kadymae]Thanks David,

I presume anacron is something I can get w/synaptic?[/QUOTE]
Yep, and it should configure itself to use any existing cron jobs when you install it.

---

