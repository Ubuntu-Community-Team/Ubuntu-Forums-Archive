---
title: "Evolution lost my calendar?!?!?!"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-17
So i've been using evolution as a calendar for the last couple months and for the most part i've been satisfied with it.  It has its quirks with repeating events but i've been dealing with that.

Anyway opened evolution today and NOTHING was there?  My calendars were still listed in the calendars section but everything i mean EVERYTHING was missing from the calendar. All of my appointments are gone!!! 

Does anybody know how to get them back?????

I really need to get everything back!!!

---

### Post by jan quark on 2008-03-17
what does this file show you

```
gksudo gedit calendar/local/system/calendar.ics
```

---

### Post by neurostu on 2008-03-17
```

user@localhost:~$ gksudo gedit calendar/local/system/calendar.ics

```
comes up blank

---

### Post by bujutsukai on 2008-03-18
I have the same issue, except that I am not being allowed to set any calendar events as well (appointments, meetings, tasks--nothing).  I also looked at the calendar file as per the above post and mine was also completely empty.  WTF???

---

### Post by bujutsukai on 2008-03-18
So I just found this other post (#663550) that says to do a backup and restore of Evolution and it will resolve the little glitch.  I tried it, and only had to do the backup part and Voila--my calendar came back.  Hope this helps!

---

