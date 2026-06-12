---
title: "Evolution DST offset"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by bwilcox on 2007-03-12
Following the DST change, the time in Evolution's calendar is 1 hour behind and all of my appointment reminders are an hour late, yet the system time is displaying correctly. Is anyone else having this issue? Is there a known fix?

I have searched both the internet and forums and have not found a solution. Thanks for any help anyone can provide.

-BW

---

### Post by darkstar62 on 2007-03-12
For what it's worth, I'm having that same issue too.  It doesn't seem like anyone thinks this is an issue just yet...

- Cory

---

### Post by infol on 2007-03-12
i guess you've double-checked your timezone? remember that not all countries change to DST at the same time... 

also, are your settings based on UTC? if so, is your BIOS clock already taking DST into account, and then your system clock reapplying or compensating for it (or however you would put it... hopefully you get what i mean)..

---

### Post by bwilcox on 2007-03-12
I've tried every combination of timezone, UTC, auto-DST, and manually setting the clock I can think of. What is strange (to me at least), is that the system clock on the desktop displays the correct time but Evolution still shows the calendar, hence all of the appointments, as one hour behind. (When you click on the system clock, the appointment dropdown reflects the same time indicated in Evolution.)

 I've tried turning the auto-DST adjust on and off within Evolution and it doesn't seem to make any difference. (For what its worth I always restart Evolution after each change to make sure it stuck). The next round will involve making changes and restarting gnome, then, if that doesn't work, restarting the system and seeing if that makes a difference.

---

### Post by Prefader on 2007-03-12
It appears that Evolution's timezone files (/usr/share/evolution-data-server-1.8/zoneinfo/<AREA>/<TIMEZONE>.ics) haven't yet been updated to reflect the changes this year - the America/New_York.ics file still shows the changes happening in April/October.  I have no idea if these can be modified without any ill effects (i.e. fudging any appointments created before the change, etc.).  I found a bug report on this (will look for a link), but didn't see a sure-fire fix.

---

### Post by Prefader on 2007-03-12
I tried changing the timezone file to match the new dates, and it did indeed shift some of my appointments.  It looks like I'd need to modify both my timezone file AND my calendar files to compensate.  :mad:

---

### Post by bwilcox on 2007-03-13
Bumping this one up in hopes for help. I haven't found anything to work yet.

---

### Post by Prefader on 2007-03-14
Fix here : [http://www.ubuntuforums.org/showthread.php?t=383560](http://www.ubuntuforums.org/showthread.php?t=383560)

It's likely that this will shift some of your appointments around, too, so you'll also need to fix up any timezone info in your calendar files (~/.evolution/calendar/local/system/) - you can just find/replace the RRULE lines as appropriate - make sure you pay attention to whether you're editing the info for DAYLIGHT or STANDARD, otherwise your appointments will be screwy.

Unfortunately, this is the best solution I've been able to find so far.  Hope it helps.

---

### Post by bwilcox on 2007-03-14
Thanks a lot for your help Prefader. Worked like a charm.

Some notes:
I'm pretty new to Ubuntu and Linux, so there were some things in the fix thread I didn't understand at first. I'll mention them here for any other newbies who come across this and get confused as well. First things first, make sure you back up any files prior to editing them, it would be bad to screw something up and not have the original to revert to.

In the fix code here: [http://www.ubuntuforums.org/showthread.php?t=383560](http://www.ubuntuforums.org/showthread.php?t=383560)

Ignore the first three lines of the script, I think they are just coding notes.

After the first three lines, the rest of the script corresponds to the lower part of the original YourCity.ics file. The "-" at the beginning of a line indicates this line should be removed and replaced by the line with a "+" at the beginning. That is basically all for that file.

Referring to Prefader's post above, the appointment calendar file in the local directory (~/.evolution/calendar/local/system/) may also need to be updated to make sure your appointment times are correct. Look for similar RRULE lines at the top of the file and just replace the BYMONTH and BYDAY parts of the line to match what you just updated in the YourCity.ics file. 

Finally, restart gnome (ctrl-alt-backspace). When you open Evolution again, everything should be back to normal.

Cheers and good luck.

BW

---

### Post by sadams6696 on 2007-03-22
I'm having a problem with my evolution alerts still being an hour off. I made the "fix" indicated in this thread regarding the /usr/share/evolution-data-server-1.6/zoneinfo/America/MyCity.ics file. The current time "red line" in the calendar is correct, as is my system time. When I make an appointment, it indicates the correct time. It's just that when I request an alarm, it pops up an hour late. Anyone else seeing this? I tried to change my ~/.evolution/calendar/local/system/calendar.ics file, but the changes kept getting "undone" whenever I made a new appointment or edited an old one. I'm using Evolution 2.6.1 under Kubuntu version 6.06 LTS.

---

### Post by bwilcox on 2007-03-22
> **sadams6696 said:**
> I tried to change my ~/.evolution/calendar/local/system/calendar.ics file, but the changes kept getting "undone" whenever I made a new appointment or edited an old one. I'm using Evolution 2.6.1 under Kubuntu version 6.06 LTS.

When you say the changes keep getting undone, what do you mean? After you make the changes and close the file, then reopen the file, are the changes still there? Or does it only happen when you try to edit the calendar?

---

### Post by sadams6696 on 2007-03-22
The changes get undone in calendar.ics only when I add/edit appointments.

---

### Post by jrjazzman on 2007-03-29
I have the same problem.  Consistently.

Worse is that appointments are intermittently showing up one hour earlier than they should.

> **sadams6696 said:**
> I'm having a problem with my evolution alerts still being an hour off. I made the "fix" indicated in this thread regarding the /usr/share/evolution-data-server-1.6/zoneinfo/America/MyCity.ics file. The current time "red line" in the calendar is correct, as is my system time. When I make an appointment, it indicates the correct time. It's just that when I request an alarm, it pops up an hour late. Anyone else seeing this? I tried to change my ~/.evolution/calendar/local/system/calendar.ics file, but the changes kept getting "undone" whenever I made a new appointment or edited an old one. I'm using Evolution 2.6.1 under Kubuntu version 6.06 LTS.

---

### Post by bwilcox on 2007-03-29
> **jrjazzman said:**
> I have the same problem.  Consistently.

Worse is that appointments are intermittently showing up one hour earlier than they should.

In what little spare time I have, I've been thinking about this and trying to replicate the problem. Unfortunately, I'm pretty new at this game and I've not had any concrete success. I'll let you know if I come across anything. One question, when you guys made your appointments did you specify a timezone for those appointments? Do you have "adjust for DST" checked in your preferences?

edit: ok, two questions

---

### Post by jrjazzman on 2007-03-29
I'm having time zone issues in Evolution, however my ics file appears to be patched.  Can someone confirm that it looks right?

```

BEGIN:VCALENDAR
PRODID:-//Ximian//NONSGML Evolution Olson-VTIMEZONE Converter//EN
VERSION:2.0
BEGIN:VTIMEZONE
TZID:/softwarestudio.org/Olson_20070227_6/America/Chicago
X-LIC-LOCATION:America/Chicago
BEGIN:DAYLIGHT
TZOFFSETFROM:-0600
TZOFFSETTO:-0500
TZNAME:CDT
DTSTART:19700308T020000
RRULE:FREQ=YEARLY;BYMONTH=3;BYDAY=2SU
END:DAYLIGHT
BEGIN:STANDARD
TZOFFSETFROM:-0500
TZOFFSETTO:-0600
TZNAME:CST
DTSTART:19701101T020000
RRULE:FREQ=YEARLY;BYMONTH=11;BYDAY=1SU
END:STANDARD
END:VTIMEZONE
END:VCALENDAR


```

---

### Post by bwilcox on 2007-03-29
Here is my code. Not sure what INTERVAL is, but mine specifies it. When I edited the file I only edited the BYDAY and BYMONTH values.

```

BEGIN:VTIMEZONE
TZID:/softwarestudio.org/Olson_20011030_5/America/Chicago
X-LIC-LOCATION:America/Chicago
BEGIN:STANDARD
TZOFFSETFROM:-0500
TZOFFSETTO:-0600
TZNAME:CST
DTSTART:19701025T020000
RRULE:FREQ=YEARLY;INTERVAL=1;BYDAY=1SU;BYMONTH=11
END:STANDARD
BEGIN:DAYLIGHT
TZOFFSETFROM:-0600
TZOFFSETTO:-0500
TZNAME:CDT
DTSTART:19700405T020000
RRULE:FREQ=YEARLY;INTERVAL=1;BYDAY=2SU;BYMONTH=3
END:DAYLIGHT
END:VTIMEZONE

```

---

### Post by sadams6696 on 2007-04-06
> **bwilcox said:**
> In what little spare time I have, I've been thinking about this and trying to replicate the problem. Unfortunately, I'm pretty new at this game and I've not had any concrete success. I'll let you know if I come across anything. One question, when you guys made your appointments did you specify a timezone for those appointments? Do you have "adjust for DST" checked in your preferences?

edit: ok, two questions

-----

I have the timezone set to america/chicago for the appointments. I don't see a "adjust for DST" box in the preferences. Are you talking about Evolution preferences? If so, where is it?

Sadly, my alarms are still coming an hour late, even now, after the "old" rules should have taken effect. Argh.

---

### Post by bwilcox on 2007-04-06
We may be running down a dead end road here, but the preferences I'm talking about are accessed through:

-> Edit
     -> Preferences
          -> Calendar and Tasks (select the box on the left hand side)
               -> Adjust for daylight saving time (checkbox under Timezone)

When I click this on and off it moves things around on my calendar by an hour. The appointments that are screwed up for you, are they recurring appointments? Have you set new appointments (with all the edits in place)? Do they also alarm 1 hour late?

---

