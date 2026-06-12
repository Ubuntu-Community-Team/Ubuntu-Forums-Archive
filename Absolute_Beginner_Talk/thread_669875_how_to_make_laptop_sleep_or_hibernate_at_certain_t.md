---
title: "how to make laptop sleep or hibernate at certain time?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by aqshin on 2008-01-16
As it says in the title, i would like to know how can i make my laptop sleep or hibernate at a particular time. I think it's done by using cron or anacron. But i don't know how to do it.

---

### Post by camnor on 2008-01-17
ok i found a way to make this work.  It seems to work perfectly fine on my laptop with no adverse effects.  So what you want to do is open up your Add/Remove programs and type in schedule in the search field and install that program and then after it downloads you want to open up synaptics and type in search hibernate and install the program with same name.  Then you want to open up the schedule application and create a new event and in the event configuration window type in for the command "sudo hibernate --force"  without the quotes then go to the reaccurrence dialog and click use advanced then go to the advanced tab and type in the minute and hour that you would like your laptop to hibernate at every day, or what day month or weekdays~!  Hope this helped! :KS

---

### Post by aqshin on 2008-01-17
Thanks for reply. I installed schedule and hibernate programs, and tried it but did not work for me. I guess it's because of "sudo" in the command line. Maybe somehow I should also provide root password to the schedule program? Actually, it would be better (linux way of doing things) to do it from the terminal. I just found "at" command to schedule tasks, but still doesn't help.

---

