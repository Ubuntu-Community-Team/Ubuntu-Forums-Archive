---
title: "Odd Sound Problem"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-05-25
OK--this is kind of strange but I have a dual boot winXP and Ubuntu each running off separate hard drives.  (I haven't yet cut the MS umbilical cord!)  Recently the[COLOR="Blue"]_ system  sounds in Ubuntu are muted compared to Windows_[/COLOR].  All audio under Ubuntu comes across as though the volume were turned way down and yet is "normal" level under Windows!  Any ideas?
This seems to have begun (coincidence or related?) after a power outage during a thunderstorm when comuter was on but not being used.  It is plugged to a surge bar but nothing else fancy.
I'm curious what could have happened!

---

### Post by Sef on 2006-05-25
> This seems to have begun (coincidence or related?) after a power outage during a thunderstorm when comuter was on but not being used

Since Windows is not affected,  I would say it is a coincidence.

> It is plugged to a surge bar but nothing else fancy.

If you have a lightening strike, it can jump the gap in the surge protector.

> I'm curious what could have happened!

A couple of things to check:

1) The icon on the taskbar: make sure the sound is not muted.

2) System > Preferences > Sound:  make sure your sound card is the default.

---

### Post by flyingsolo on 2006-05-26
Problem Solved!  I went to Applications-->Sound & Video-->Volume Control to find the "PCM" level was zero.  (Master & Headphone levels were high)  So Just set the PCM level to mid range, e voila!  Sound restored.  However, I still don't know how it got reset in the first place.  Anyway, it's fixed.

---

### Post by Lord Illidan on 2006-05-26
Strange, no? Also check the wave in alsamixer (type it in a terminal).

---

