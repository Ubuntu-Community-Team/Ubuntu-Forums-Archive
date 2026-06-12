---
title: "Time! It's too expensive..."
date: 2009-08-31
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2009-08-31
I've always had this issue where I have to re-sync the date and time in Windows, Ubuntu, and OS X. Ubuntu used to be quite reliable, but since I installed 9.04, it doesn't ever seem to be right.

A. I know how to re-sync the time in Windows and OS X. How do I do it in Ubuntu?

B. Any clue why this happens? I assume it has to do with system time and how each OS interprets it, but I would like a few more specifics, if anyone knows.

---

### Post by tgalati4 on 2009-08-31
Linux normally stores UTC (universal coordinated time, what used to be Greenich Mean Time GMT) in the system BIOS.  The operating system reads your timezone and displays the correct time:

date

cat /etc/timezone

Windows stores local time in the system BIOS, so when you dual-boot, the time gets messed up.  I believe there is a switch to tell windows that system time is UTC/GMT.  This normally fixes it.

I think OS X works similar to Linux, storing time as UTC/GMT.

To fix the time once, use ntpdate:

sudo ntpdate ntp.ubuntu.com

This normally happens at linux boot.  The configuration is found in /etc/default/ntpdate.

---

### Post by Tu1J4kXk8NUhMz on 2009-09-01
I'll have to check into that switch. This makes sense, as I am not automatically on the internet when I boot up. Thanks!

---

