---
title: "Running mythfilldatabase at a set time"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by qrazi on 2007-01-28
Currently I am running mythfilldatabase manually about every two days. Mythfilldatabase is a little program to grab Tv guide data for MythTV.

MythTV has an option to run automatically at a set time, but that keeps on giving me failed errors. I understand that this option isn't working properly (yet).

I also think Ubuntu provides a way to run programs at set times, but i have not really an idea what i need, and how to configure it. Could anybody point me in the right direction, or even give the answer straight away?

---

### Post by davmac on 2007-01-28
What you need is cron. Have a look at [http://www.ubuntuforums.org/showthread.php?t=102626]("http://www.ubuntuforums.org/showthread.php?t=102626") for more info.

BTW: I just have the mythfilldatabase script in /etc/cron.daily and it automatically runs itself every morning at 7:30 with no problems.

Hope this helps,

Dave Mac

---

### Post by qrazi on 2007-01-30
Thank for the link. I will see tomorrow if it actually worked. MythTV apprantly automatically installed a cron job, but used a wrong location for the mythfilldatabase executable.

/edit: mythfilldatabase indeed ran properly... now i should always have my guide data up to date

---

