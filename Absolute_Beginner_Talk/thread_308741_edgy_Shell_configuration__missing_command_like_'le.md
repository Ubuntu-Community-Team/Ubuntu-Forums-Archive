---
title: "edgy: Shell configuration / missing command like 'let' with sh"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by okuhl on 2006-11-28
Hi,

I installed edgy on my server some days ago and used ipkungfu to get an easy firewall configuration. When trying to call ```
# ipkungfu
``` on the shell as root user (I did a sudo -i before), I got error messages and found out that the command 'source' was missing. I changed the shell in /usr/sbin/ipkungfu to '#!/bin/bash' and everything works fine.

Today I installed apticron and wanted to check if I will get an email. But calling ```
# /etc/cron.daily/apticron
``` results in the error "/etc/cron.daily/apticron: 6: let: not found" - and again is a problem with sh.

Does anyone have a hint for me if I missed something? Or is Ubuntu configured in another way so the scripts are not compatible? How could I change this?

THX for the help!

Regards,
    Oliver.

---

### Post by po0f on 2006-11-28
okuhl,

```
[FONT="Courier New"]sudo dpkg-reconfigure dash[/FONT]
```

---

### Post by NESFreak on 2006-11-29
same problem
tried it. Found out that selecting no was the answer, instead of dash being the solution. Did the trick for me tnx

---

### Post by okuhl on 2006-12-10
> **NESFreak said:**
> Found out that selecting no was the answer, instead of dash being the solution.

Yes, this works for me, too. Thanks for the help! :-D

---

### Post by Buggin on 2006-12-15
thank god... i've been looking through the forums for this all day

---

