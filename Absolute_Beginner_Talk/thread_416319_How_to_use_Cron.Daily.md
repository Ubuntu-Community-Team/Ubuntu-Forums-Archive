---
title: "How to use Cron.Daily?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by djseto on 2007-04-21
I added some scripts to the /etc/cron.daily/ folder for mythtv, but they dont seem to be running everyday. Is there something I am missing besides just dropping the scripts in there? I thought there would be a file where I define what time I want them run, but from what I read in the MythTV wiki, it just says to add them to my cron.daily folder. That clearly isnt working.

---

### Post by gabkdlly on 2007-04-22
Did you make your scripts executable?

chmod uog+x file

I usually schedule tasks using a crontab.

crontab -e

As always, the manuals can be helpful

man chmod
man crontab

Also, to be on the safe side, your scripts should declare in the first line which program should be used to run them. Making the first line of your scripts look like this should suffice.

#!/bin/bash

Actually, I hardly use the cron.daily and company folders, so I can't guarantee that this is the source of your problems, just some thoughts on what you can try. Please report back if one or both of these fix your problem.

Cheers

---

