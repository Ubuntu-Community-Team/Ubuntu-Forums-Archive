---
title: "Lightning in Thunderbird 2 - events are of by 6 hours"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by robertpolson on 2007-04-26
I cannot figure out if it is Ubuntu or Lightning.

But when I import events from the mycalendar.ics file all of the events show up fine.

About a 1 day later all of them are off by 6 hours. Both Lightning and Ubuntu are set to the correct Time Region. And this always happens no matter how many times I delet and reimport my events.

What is going on ?

---

### Post by John the train on 2007-04-26
I've seen references to a similar problem between Windows and Linux in a dual-boot, which is connected to the UTC ( Universal Time Constant ) option, so it might be worth checking if Lightning and your main clock are using the same settings.

---

### Post by robertpolson on 2007-04-26
You mean like PM/AM vs 24hour clock ?

I have my Ubuntu set to 24 hour whereas Lightning is set to PM/AM

I will see if I change this in lightning.


Edit: It seems that Lightning does not have the option to display in the 24 hour time format which sucks. I have to switch everything to AM/PM and see if it will work.

If anyone knows how to set Lightning to display 24 hour format, let me know.

---

### Post by robertpolson on 2007-04-28
I still have the same problem.

Even after setting everything to AM/PM time format, after 1 day all of the events have moved 5 hours ahead. 

Any ideas?

---

### Post by silkstone on 2007-04-28
AFAIK there is no way to alter the time format in Lightning, except by altering the regional settings for the computer. When I first installed Edgy everything was set to US defaults instead of UK for some reason, and the times showed as AM/PM rather than 24-hour clock on both the top panel and in Thunderbird/Lightning. I couldn't find any way to alter this, but when I changed the region/language settings to UK (where I am!) this also switched everything to 24-hour clock as well as European date format (dd/mm/yy).

Sorry I can't be of any more help.

---

### Post by robertpolson on 2007-04-29
This was posted in the mozilla newsgroup:

> Most likely your calendar-file has a VTIMEZONE which can't be matched against one of the mozilla-zones. When importing it stayus in memory with the offsets which were provided by the mycalendar.ics. After restrating thunderbird the events are set to UTC and show up on UTC time. This is a known problem for which a solution is being developed. Up till a couple of days ago this was blocking 0.5 but as it will have such a huge impact on the code, it was decided to release an 0.5.x - version soon after 0.5 comes out.

Meanwhile, what you could do is open the ics in a text-editor and replace the timezone with a mozilla-one, both the VTIMEZONE-part and the parts in DTSTART, DTEND, VALARM etc. A simple search and replace should do the trick... After this you can import the calendar...

---

