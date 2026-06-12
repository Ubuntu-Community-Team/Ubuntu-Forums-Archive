---
title: "Time incorrect in Gutsy"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by pumpkinpapa on 2008-01-22
I have a clean install of Gutsy on a Inspiron 1100, my connection is by wireless through a proxy on a dialup internet.
I suspect this is why my NTP won't work properly. I am in Eastern time but when I select "synchronize with internet servers" it fails. Resetting the clock manually fails as well. The BIOS is accurate though, as is the XP boot as well.
I have switched to other time zones but none work.
What might be wrong?
Is there a way to manually configure NTP?

---

### Post by p_quarles on 2008-01-22
How far off is the time? I suspect you may have set Ubuntu to use UTC rather than your local time, and that your CMOS is tracking local time, hence the confusion. 

To make certain, try these commands:
```
date -u
```
and
```
date -R
```
Does the output of either one correctly match the current EST?

---

### Post by mikeyphi on 2008-01-22
Are you saying that you are unable to change timezone through the System/Administration/Time and Date GUI?
OR
When you say that you've switched to other timezones but none work - is it just the Internet Time synchronization not working?

---

### Post by pumpkinpapa on 2008-01-22
Ok I checked the box for "Use UTC" in the preferences and that moved the time up from 8:24 to 1:24. But when I try to adjust the time and date it still shows the time as 8:24 when done manually or automatically.

---

### Post by pumpkinpapa on 2008-01-22
> **p_quarles said:**
> How far off is the time? I suspect you may have set Ubuntu to use UTC rather than your local time, and that your CMOS is tracking local time, hence the confusion. 

To make certain, try these commands:
```
date -u
```
and
```
date -R
```
Does the output of either one correctly match the current EST?

For date -u I got "Tue Jan 22 13:31:21 UTC 2008" and for date -R I got "Tue, 22 Jan 2008 08:31:58 -0500"

Now I am using a 12 hour clock as well, if that helps any :)

---

### Post by p_quarles on 2008-01-22
Looks like my hunch was correct. Your system is behaving as though the time set in your CMOS is UTC (aka Greenwich Mean Time), whereas it's actually on local time. 

It's been a while since I had to fix a similar problem, but this is what I recall. You'll need to reset the OS's understanding of what constitutes UTC, by adding five hours to it. So, if the current time according to "date -u" is 13:45:00, run this:
```
sudo date -u 01221845
```
This *may* cause permissions problems on some recently modified files, but that can be fixed if it occurs.

---

