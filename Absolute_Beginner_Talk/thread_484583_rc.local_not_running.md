---
title: "rc.local not running?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by kspn on 2007-06-25
I want to run a script (3 commands actually) and so I put them into the rc.local file as was indicated in another post. 

However I noticed that the commands don't seem to be running, they are commands to mount 3 network shares that I want constant access to.

*Adding the hard drives to the Xubuntu system is not an option because I think that the PSU might complain about having an additional 3 Hard drives plugged in as well as the lack of Connections.*

As a temporary workaround I have put the command in my **cron**
```
@reboot mount ....
```

Any suggestions on how to get rc.local working (I would prefer that to the cron variant)

---

### Post by yabbadabbadont on 2007-06-25
Try removing the "-e" option from the "#!/bin/sh" line at the top.

Edit: If that doesn't work, try switching the default shell to be bash instead of dash (dash is used by default on feisty)  "sudo dpkg-reconfigure dash"  Answer no when it asks if dash should be the default shell.

---

### Post by kspn on 2007-06-26
Thanks for the rapid response :)

I will try that when I get home from work.

Rebooting my PC to test it is a little annoying but... *shrug*

---

