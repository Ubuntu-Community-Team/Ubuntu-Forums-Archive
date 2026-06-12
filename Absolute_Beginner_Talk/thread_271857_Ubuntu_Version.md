---
title: "Ubuntu Version"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Jareth on 2006-10-05
I just noticed something in my Repositories list in Synaptic.

It says 5.10 next to everything rather than 6.06 which I'm sure it used to say.

Any idea why thats different now? I installed ubuntu off a 6.06 CD.

---

### Post by GlennB on 2006-10-05
Hi,

> **Jareth said:**
> I just noticed something in my Repositories list in Synaptic.

It says 5.10 next to everything rather than 6.06 which I'm sure it used to say.

Any idea why thats different now? I installed ubuntu off a 6.06 CD.

Can you post the contents of the file:

```
/etc/apt/sources.list
```

Also note the date and time when this file last changed. It may give you a clue. While you're there, do a quick 'ls' in the /etc/apt directory to see if you have any backups of the sources.list file hanging around.

Could you have installed any scripted update tools lately? I'll take a wild guess that something's been tinkering with your repos. list.

Regards,

Glenn.

---

