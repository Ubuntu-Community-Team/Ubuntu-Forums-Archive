---
title: "How to &quot;restart&quot; apps/services?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-06-20
I would like to know the command for restarting a program, besides killing it and letting it start itself.  I know about "kill <processID>" and going "top" and killing it from there, but what would a command be to just kill something by name maybe?

Reason for this is I want to make a little botton/launcher on the panel that will restart it (the panel).

---

### Post by drivel on 2007-06-20
What do you wanna to restart?
As a app/services,you can
'sudo /etc/init.d/XXXXXXX restart'
Always,app/services start script save at /etc/init.d/

---

### Post by NeoLithium on 2007-06-20
Perhaps you mean killall gnome-panel?

---

### Post by ryanVickers on 2007-06-20
Thanks!  wow, that was easy. :p

---

### Post by drivel on 2007-06-20
Dependency will make drive you up the wall~
Do not kill gnome-panel,restart X is a good choose

---

### Post by drivel on 2007-06-20
> **ryanVickers said:**
> Thanks!  wow, that was easy. :p

Also,'service XXXXX' is useful for services.

---

