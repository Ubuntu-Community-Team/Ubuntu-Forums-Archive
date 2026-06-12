---
title: "[SOLVED] Adept problem"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by ukemike on 2007-11-09
When I go to run adept package manager it tells me that another process is using the adept database.  But it says this even immediately after booting.  I haven't updated anything in a while, and I wanted to install some new programs, but I can't.  I did a ps -e in the terminal but the only process that looked adept related was soemthing like adept_notifier.  That is probably the process that monitors when packages need updating.  Oh this isn't the newest version of Kubuntu, but the last version.

---

### Post by overdrank on 2007-11-09
> **ukemike said:**
> When I go to run adept package manager it tells me that another process is using the adept database.  But it says this even immediately after booting.  I haven't updated anything in a while, and I wanted to install some new programs, but I can't.  I did a ps -e in the terminal but the only process that looked adept related was soemthing like adept_notifier.  That is probably the process that monitors when packages need updating.  Oh this isn't the newest version of Kubuntu, but the last version.

Hi have you tried to update through the terminal and see if you get any errors
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ukemike on 2007-11-09
THANX

okay I tried apt-get from the konsole.  The last line seems most relevant:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

now it's outputting lots of lines that read like: Setting up openoffice...

now it's done and it ran into dependency problems with kdesktop, kdm, konqueror

should I run the apt-get again?

---

### Post by overdrank on 2007-11-09
> **ukemike said:**
> THANX

okay I tried apt-get from the konsole.  The last line seems most relevant:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

now it's outputting lots of lines that read like: Setting up openoffice...

now it's done and it ran into dependency problems with kdesktop, kdm, konqueror

should I run the apt-get again?

If you ran the command ```
sudo dpkg --configure -a
``` and still having trouble then you may want to make sure your repos are enabled.

---

### Post by ukemike on 2007-11-09
well I did run apt-get update again, and it ran very quickly, and didn't seem to update anything.  However I just ran Adept again and it seems to be functioning correctly now.

Thanks

---

### Post by overdrank on 2007-11-09
> **ukemike said:**
> well I did run apt-get update again, and it ran very quickly, and didn't seem to update anything.  However I just ran Adept again and it seems to be functioning correctly now.

Thanks

Great and please mark the thread as solved under thread tools and good luck! :popcorn:

---

