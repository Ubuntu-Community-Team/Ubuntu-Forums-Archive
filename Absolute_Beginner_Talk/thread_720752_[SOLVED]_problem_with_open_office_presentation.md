---
title: "[SOLVED] problem with open office presentation"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by mlawson4 on 2008-03-10
my open office presentation will not open.  everything else works great, but i really need this to open for class this week. the splash screen appears and freezes on the screen.

---

### Post by acirilo on 2008-03-10
U r opening an existing file? Or just the program?

---

### Post by mlawson4 on 2008-03-10
just opening the program. i tried reinstalling, but that didn't work either.  however, i just put a new theme on my laptop from gnome-look could that bring about this problem.

---

### Post by acirilo on 2008-03-10
i'm so freakin new with ubuntu.. i'm not much help..but try to poke around your log files..see if anything jumps out at you..


cat /var/log/apport.log
cat /var/log/messages

examples:
tail -f /var/log/apport.log
more /var/log/xorg.0.log
cat /var/log/mysql.err
less /var/log/messages
grep -i fail /var/log/boot

here is a URL that might help explain this some.

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

---

### Post by mlawson4 on 2008-03-11
i figured it out and it was because of the theme that i downloaded.  i planned on making an original theme anyway so this will just speed up the process.  thank you.

---

### Post by acirilo on 2008-03-11
AWESOME!! i wish i could have been more help.. i'm just learning myself.

Yes sometimes a roadblock is the best thing to happen..forces us to learn something else.

---

