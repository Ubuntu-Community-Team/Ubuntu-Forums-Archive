---
title: "[SOLVED] Using  /var/log/messages"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by keith1 on 2007-11-09
I'm trying to track down an error message from a couple of days ago - but I can't figure out how to go back in the logs. I can only see todays log. How do I go back to a previous date to check message logs?

Thanks,   Keith

---

### Post by poudin on 2007-11-09
hey..they should be there up to a certain point...they get gzipped by logrotate.....it keeps the last 7 days i think by default..

syslog1-6.gz

---

### Post by keith1 on 2007-11-10
For some reason I can't go back more than one day. I'm new to this area so it could be something I'm doing wrong, but I've tried every way I can think of.

Thanks,   Keith

---

### Post by jhenager on 2007-11-10
Places>Home Folder
Under File System, browse to /var/log
Doubleclick one of the .gz files
Right click the ungzipped file, and choose Open With "Text Editor"

---

### Post by keith1 on 2007-11-11
jhenager - That did the trick!  The thumbnail was very helpful in navigating my way through the directions.  I'm very glad I joined this board.

Thank you very much,      Keith

---

