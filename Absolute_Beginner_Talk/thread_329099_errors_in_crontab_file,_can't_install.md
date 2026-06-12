---
title: "errors in crontab file, can't install"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by hallmerle on 2006-12-31
I thought I had successfully installed crontab for user family, though I don't remember specifying the user at the time.  It's purpose was to run a simple backup.sh to rsync /home to a different mounted drive (which works manually, just fine).  I thought I'd set it up to run Saturday mornings and I've verified that it's not running as it hasn't done so.

If I

[INDENT]crontab -e[/INDENT]

while logged in as family, I get a different crontab than the one I had created.  This one has /etc/crontab at the top of the file and says it's the system-wide crontab.

If I

[INDENT]sudo ls /var/spool/cron/crontabs[/INDENT]

it lists family as the only result.

[INDENT]find / -name "crontab"[/INDENT]

yields two results:

[INDENT]/etc/crontab
/usr/bin/crontab[/INDENT]

And if I

[INDENT]crontab -u family /usr/bin/crontab[/INDENT]

I get

[INDENT]"/usr/bin/crontab":0: bad minute
errors in crontab file, can't install.[/INDENT]

So, assuming that whatever I did to it can't be fixed, I'd think I should remove it using -r and start all over again.  But just to make sure I'm removing the right one, I do

[INDENT]crontab -u family -l[/INDENT]

whereupon it displays the system-wide crontab file which, I assume, I really shouldn't remove.

I'm confused.  Can anyone make sense of this for me?

Merle

---

