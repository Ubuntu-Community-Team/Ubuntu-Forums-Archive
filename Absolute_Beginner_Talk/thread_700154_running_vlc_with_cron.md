---
title: "running vlc with cron"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by thbrandston on 2008-02-18
Hey,
  I've been trying to turn my computer into an alarm clock and have spent upwards of six hours reading all the cron literature and cron-related posts I can find and I cannot get it to work.

```

# m h  dom mon dow   command
 */15 * * * * date >> ~/test
 * * * * * export DISPLAY=:0 && usr/bin/vlc -f /home/mylogin/alarm.avi ; date >> ~/test2

```

this is my cronfile both test statements work, ~/test and ~/test2 both get updated when they're supposed to be, but vlc does not run.

 I've tried using wxvlc instead of vlc, it doesn't work.  I've tried putting my name in /etc/cron.allow , is there a special syntax for that file? or can you just type "mylogin" in there?  I'm not sure what else to try.

any suggestions?

---

### Post by njparton on 2008-02-18
I don't have any specific cron/vlc suggestions but can I suggest that you put that command into a bash script, make it executable and then just call that from cron?

It will be much easier to tweak then and you can call it from your home folder and will retain a copy for the future if you ever upgrade etc.

Just a suggestion :)

---

### Post by njparton on 2008-02-18
Actually, one suggestion: try running it from sudo's cron, not your own:

```
sudo crontab -e
```

---

### Post by thbrandston on 2008-02-18
when I try to use sudo crontab -e it says "you (root) ar not allowed to use this program (crontab)"

I've also never done anything with bash scripts before and that will probably just leave more places for errors. 

anything else I could try?

---

### Post by kpkeerthi on 2008-02-18
Path to vlc appears to be incorrect **usr/bin/vlc** should be **[COLOR="Red"][B]/**[/COLOR][/B]usr/bin/vlc

---

### Post by njparton on 2008-02-18
> **thbrandston said:**
> when I try to use sudo crontab -e it says "you (root) ar not allowed to use this program (crontab)"

I've also never done anything with bash scripts before and that will probably just leave more places for errors. 

anything else I could try?

You're bash script would be really simple:

```
#!/bin/bash
export DISPLAY=:0 && /usr/bin/vlc -f /home/mylogin/alarm.avi ; date >> ~/test2
```

make it executable with chmod and away you go!

---

