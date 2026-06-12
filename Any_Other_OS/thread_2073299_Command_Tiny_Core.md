---
title: "Command Tiny Core"
date: 2012-10-19
forum: Any Other OS
---

### Post by Rebecca Chong on 2012-10-19
When I login as root in terminal, and type apt -get install cron, it shows not have this command.why? 
my problem is want to install cron but this command can't use. Izit have the other command to install cron? Because I want doing cronjob. Please help me...Thanks:confused:

---

### Post by zombifier25 on 2012-10-19
What Linux distro are you using? Is it Tiny Core? I don't think it comes with apt.

EDIT: Just checked. If you want to install apps, [see here](http://distro.ibiblio.org/tinycorelinux/download_howto.html).

EDIT2: See SlugSlug's post below.

---

### Post by SlugSlug on 2012-10-19
cron should be installed by default

to edit the user's cron use
```
cron -e
```

---

### Post by howefield on 2012-10-19
Thread moved to "*Other OS/Distro Talk*"

---

### Post by Rebecca Chong on 2012-10-19
is tiny core

---

### Post by Rebecca Chong on 2012-10-19
apt-get command not found~

---

### Post by mikewhatever on 2012-10-19
Lots of distros use apt, and many don't. Tiby Core happens to be among the latter.

---

