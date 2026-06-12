---
title: "can't see winxp partition anymore"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by paolone on 2005-08-25
hi all, i'm totally new in linux!
i made my new partition from windows xp, installed ubuntu, that works very good, but there is no way to reboot my notebook back to windows, and i need it...
when i choose xp as op system at starting, it comes at a point where i can read just "autochk program not found - skipping autocheck" then the system restart and boot and reboot forever, if i dont run linux... maybe the windows partition is hidden or something like that, but how can i change it and get out of this problem.
i'm a new linux user, so, if you could help me, please be patient and explain me in an easy way what i need to do.
thanx all in  advance,
paolo

---

### Post by davmac on 2005-08-25
[QUOTE=paolone]...it comes at a point where i can read just "autochk program not found - skipping autocheck" then the system restart and boot and reboot forever[/QUOTE]

There's a discussion of this error message at [http://www.techspot.com/vb/topic7746.html](http://www.techspot.com/vb/topic7746.html). Does this shed any light for you?

HTH,

Dave MacLeod

---

### Post by paolone on 2005-08-26
thanx dave, but i cannot find any solution, maybe coz i'm not enough experienced in linux.... i'd like to run an application like partition magic in linux to manage the partition of windows, but i have no idea of what application to use, how to install it in linux and so on. in other words i'm in trouble...
ciao and thanx again

---

### Post by Kapre on 2005-08-26
[QUOTE=paolone]hi all, i'm totally new in linux!
i made my new partition from windows xp, installed ubuntu, that works very good, but there is no way to reboot my notebook back to windows, and i need it...
when i choose xp as op system at starting, it comes at a point where i can read just "autochk program not found - skipping autocheck" then the system restart and boot and reboot forever, if i dont run linux... maybe the windows partition is hidden or something like that, but how can i change it and get out of this problem.
i'm a new linux user, so, if you could help me, please be patient and explain me in an easy way what i need to do.
thanx all in  advance,
paolo[/QUOTE]

Paolone - What did you use to partition your notebook HD? There are some ways that you need to do before partitioning your XP drive and use the remaining size. if you only have 1 HD (say 40 gig) and you see that there is still 30G remaining and you want to use 15G for ubuntu, you must defrag it at least 2 times before partitioning (why? - because Windows files are scrattered all over your HD).

I'm not so sure on how you can return back to XP if you did not do a defrag before partitioning. I hope there is still a workaround on this instead of re-installing your XP.

K

---

### Post by paolone on 2005-08-26
thank you all, i solved the problem.
it was easy enough after all (if i could make it, it was extremely easy).
i downloaded a free tool for dos (mbrtool.exe), then i started the system in dos mode using a system disk, from dos i ran that tool and i could "unhide" the windowsXP partition that was the real problem.
if you need some further information just mail me at [email]paolone2001@gmail.com[/email]
ciao  :)

---

