---
title: "F-keys changing behavior with every update!"
date: 2010-06-21
forum: Apple Hardware Users
---

### Post by Freek07 on 2010-06-21
Hey guys,

I'm using ubuntu 10.04 on mbp 5.1 and change of FN/F behavior after _EVERY_ kernel update is getting really ridiculous.

On update "a", I gey F-keys without FN; after upgrade to kernel "b", I get media keys by default, then again F,...

I _really_ don't want to change pommed.conf after every reset (and re-reset it) :mad:

---

### Post by JohnAtilano on 2010-06-21
> **Freek07 said:**
> Hey guys,

I'm using ubuntu 10.04 on mbp 5.1 and change of FN/F behavior after _EVERY_ kernel update is getting really ridiculous.

On update "a", I gey F-keys without FN; after upgrade to kernel "b", I get media keys by default, then again F,...

I _really_ don't want to change pommed.conf after every reset (and re-reset it) :mad:

Exact same specs; exact same issue.  Drives me crazy.  Unfortunately I don't know how to change pommed.conf.  Can you post a tutorial.

I prefer standard function keys (F1 - F12) while using  "fn" + F# for media / settings keys.

---

### Post by Freek07 on 2010-06-21
The problem is, the kernel changes behavior- in version A, option "1" means "WITH FN", in version B, it means "WITHOUT FN"- so, I guess the guys are jerking with the kernel.

Anyway, option for FN-key behavior is in /etc/pommed.conf, first option:

# General configuration
general {
        # fnmode: functions keys first (no need to use fn) or last
        # Value is either 1 or 2, effect is hardware-dependent
        fnmode = 2
}

---

