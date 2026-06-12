---
title: "evolution-alarm-notify running but still no alarms"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by bdk6m2007 on 2007-07-31
evolution-alarm-notify is running but I'm still not getting alarms from my exchange server after I log in.

I've found that if I create an entry in the local calendar, set an alarm, and let that alarm happen I do get the local alarm and from that point on I'm getting my exchange alarms properly - doing this every time I login is ***really*** annoying.

Has anyone else seen this behavior or have any tips?

---

### Post by linuxwizard on 2007-08-01
I don't use Evolution but look here you might find some documentations that will help.

[http://www.gnome.org/projects/evolution/](http://www.gnome.org/projects/evolution/)

---

### Post by TheOrangeRider on 2008-02-05
I'm having a somewhat similar issue. My personal calendar alarms work fine, but my Exchange calender will not give me any alarms whether I set an alarm locally or not. I noticed if I do a gconf-editor /apps/evolution/calendar/notify/calendars, the list is empty. Should there be something in this list?

EDIT: I found that if I go to Edit->Preferences->Calendar and Tasks->Alarms, and uncheck and recheck the box for my Exchange Calendar, it works. But I have to do this every time I start Evolution

---

