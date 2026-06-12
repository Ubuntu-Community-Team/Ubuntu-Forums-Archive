---
title: "enabling automatic updates"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-12-01
I am using kubuntu 6.06
I had disabled the automatic updates.

now from where do I enable them

---

### Post by nixternal on 2006-12-02
How did you disable the automatic updates? Did you remove the apt or aptitude files from /etc/cron.daily? Did you just disable the notifier in the task bar? If you simply closed out of the notifier in the taskbar, your auto updates still occur daily, you just don't get notified. If that is the case, then simply press Alt+F2, and type adept_notifier and press enter/ok. This should fire up the notifier and should start notifying you of updates. Now if you removed apt from cron.daily then you need to replace that file. If so, let me know and I will paste it if you need it.

---

