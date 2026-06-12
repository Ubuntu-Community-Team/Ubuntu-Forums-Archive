---
title: "digikam not working"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Corvair on 2008-02-19
I have installed digikam and I cannot import photos. Did I miss something during the installation? This is the message I get:


Error digikam

Cannot talk to klauncher

I am using Ubuntu 7.10

---

### Post by amingv on 2008-02-19
Try this in the console:
```
kdeinit
```

Or try to restart X (Ctrl+Alt+Backspace).

---

### Post by Corvair on 2008-02-19
amingv,

Still same error,
This is what I get:

claude@claude-desktop:~$ sudo kdeinit
Error: "/tmp/ksocket-claude" is owned by uid 1000 instead of uid 0.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/claude/.DCOPserver_claude-desktop__0
and start dcopserver again.
---------------------------------

kdecore (KLocale): WARNING: Definition of PluralForm is none of NoPlural/TwoForms/French/OneTwoRest/Russian/Polish/Slovenian/Lithuanian/Czech/Slovak/Arabic/Balcan/Macedonian/Gaeilge/Maltese: Definition of PluralForm - to be set by the translator of kdelibs.po
kdeinit: Communication error with launcher. Exiting!
claude@claude-desktop:~$

---

