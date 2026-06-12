---
title: "Firefox doesn't work after Automatrix completes"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-03-24
Hi, I installed Automatrix and ran the script to install everything including the updated version of forefox.  I rebooted the computer, now firefox will not start.  I run /usr/bin/firefox and it says something is missing.  But, I run /usr/bin/firefox.ubuntu and it does work.  What is going on?  Thanks!

---

### Post by arnieboy on 2006-03-24
[QUOTE=echo $USER]Hi, I installed Automatrix and ran the script to install everything including the updated version of forefox.  I rebooted the computer, now firefox will not start.  I run /usr/bin/firefox and it says something is missing.  But, I run /usr/bin/firefox.ubuntu and it does work.  What is going on?  Thanks![/QUOTE]
please paste the results of the following command:
```
firefox 
```
from terminal

---

### Post by echo $USER on 2006-03-24
I can't right now; I'm at work.  Once I get home I'll repost.

---

### Post by trent dillman on 2006-03-24
I think Automatix installs firefox in /opt/firefox, so try running

```
/opt/firefox/firefox
```

Or try this:

```

mv ~/.mozilla ~/.mozilla_backup

```

NOTE: This will temporarily move any bookmarks and whatnot you had...

---

### Post by echo $USER on 2006-03-24
******@ubuntu:/usr/bin$ firefox
bash: firefox: command not found
******@ubuntu:/usr/bin$ whereis firefox
firefox: /usr/bin/firefox.ubuntu /usr/bin/firefox /usr/lib/firefox /usr/bin/X11/firefox.ubuntu /usr/bin/X11/firefox /usr/share/man/man1/firefox.1.gz
******@ubuntu:/usr/bin$ which firefox
******@ubuntu:/usr/bin$ firefox.ubuntu
*** loading the extensions datasource
******@ubuntu:/usr/bin$

This is waht i get when i run /usr/bin/firefox and /usr/bin/firefox.ubuntu

This is version 1.0.7 I am using to post to this thread.  I'm more of a Opera fan any way.  Opera works to perfection after I installed Automatrix.  Thanks for the help me try to remedy Firefox.

---

### Post by arnieboy on 2006-03-24
try running the "firefox 1.5" option (and only that option) from automatix again. It seems like the file did not get downloaded for some reason. If it works, well and good. if it does not then we need to diagnose the problem more closely.

---

### Post by echo $USER on 2006-03-25
[QUOTE=arnieboy]try running the "firefox 1.5" option (and only that option) from automatix again. It seems like the file did not get downloaded for some reason. If it works, well and good. if it does not then we need to diagnose the problem more closely.[/QUOTE]

Worked like a charm.  Thanks for all the help.

---

