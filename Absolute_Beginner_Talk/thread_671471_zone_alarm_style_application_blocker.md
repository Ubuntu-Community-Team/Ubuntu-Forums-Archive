---
title: "zone alarm style application blocker"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2008-01-18
Is there an equivalent for Ubuntu to the feature of ZoneAlarm that allows you to know which applications are trying to access the internet and allow or deny them on a case-by-case basis?

---

### Post by NullHead on 2008-01-18
There is firestarter for gnome or there is also guarddog for kde.

---

### Post by thelatinist on 2008-01-18
What applications are you worried about?  I don't think there's anything in the repositories that you need to be concerned about.

---

### Post by zipperback on 2008-01-18
> **dinostabOMG said:**
> Is there an equivalent for Ubuntu to the feature of ZoneAlarm that allows you to know which applications are trying to access the internet and allow or deny them on a case-by-case basis?

guarddog
watchdog
guidedog

Check those out and see if they fit your needs.

- zipperback
:popcorn:

---

### Post by some_random_noob on 2008-01-18
> **NullHead said:**
> There is firestarter for gnome or there is also guarddog for kde.

But those are based on port and ip filtering - they don't block specific programs (As far as I know). One thing though, is to look at the "active connections" in Firestarter (You'll need to be an admin to view it though).

Alternatively:

> netstat -lntp

I don't know if you can block specific programs, but you can certainly view what's going on if you have an admin account. Then again, if you don't want a program connecting to the internet then just close it.

---

### Post by bodhi.zazen on 2008-01-18
Those apps should not be used to monitor your network as the run as root and thus are a security risk.

In a nutshell, no there is nothing similar, but Linux is not windows either.

I would steer you here : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

And to AppArmour

---

### Post by dinostabOMG on 2008-01-18
I thought it might be like that. To be specific, though, it's actually Wine that I don't want connecting to the internet. :)

---

### Post by scorp123 on 2008-01-18
> **dinostabOMG said:**
>  it's actually Wine that I don't want connecting to the internet. :) Well ... that highly depends on what you're running inside of Wine. Wine itself won't do anything "funny".

If you really want tight control over who a Windows program is talking to, then I'd suggest to use VMware Server (it's available via the "Canonical partner" repos), and then set the Windows guest OS to "host only" networking, meaning that it can only talk to your Linux machine but not to anyone or anything else.

---

### Post by thelatinist on 2008-01-18
> **dinostabOMG said:**
> I thought it might be like that. To be specific, though, it's actually Wine that I don't want connecting to the internet. :)

If you renamed winsock32.dll, I'm pretty sure no windows app could access the Internet.

---

### Post by Vadi on 2008-01-18
Or Virtualbox, which is open-source and is avialable in repositories.

-chin- wine runs it's programs as separate processes. Maybe you can use firestarter somehow to block them.

---

### Post by some_random_noob on 2008-01-18
> **dinostabOMG said:**
> I thought it might be like that. To be specific, though, it's actually Wine that I don't want connecting to the internet. :)

Then use Firestarter and do a whitelist. On my installation all I allow is the following out-going ports: HTTP, HTTPS, MSN. I imagine that only allowing those ports would limit any "dodgyness".

---

