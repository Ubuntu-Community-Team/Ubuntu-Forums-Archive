---
title: "gnome-schedule or Cron in general"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by kyle.quamme on 2006-09-10
ok, so I've tried to use "crontab -e" to schedule cron to run xmms as my alarm in the morning. I setup the cron.allow list, but cron didn't seem to work. I then read about using the argument for GUI apps, but that didn't work either.

So then I tried gnome-scheduler and that didn't work. The only thing I have gotten to work was the KDE scheduler. Any ideas?

---

### Post by kyle.quamme on 2006-09-10
ok, so I peeked into /var/log/syslog and it shows that cron ran the command, so now I'm wondering what I can do to get it do run xmms.

Should I point it to a script which then in turn opens xmms?

---

