---
title: "Login: Error creating child process"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Sugz on 2008-01-04
So after updating my system, 140 files. Which was odd, i tried to log into my normal user and the following error message appeared as well a blank terminal.

"There was an error creating the child process for this termina"

When i Ctrl+Alt F3 to log in using command line, i got endless lines of

Bash: /dev/null Permission denied.

I hunted around and found a temporary solution but when i log in, all i get is a mesage saying that my session lasted no longer then 10 seconds. 

My Root login works, but cannot use wireless as the device manager only recognises my Processors etc.. ** I think i updated files that i should not have**

I have tried to crete a new user but the same error is created. 

Please, any help, i am using Wubi, Feisty with the default kernel.



**If in the worst case scenario i need to re-install Ubuntu, how would i keep all my themes, settings, sounds etc. because i have worked hard getting ubuntu to run the way i like it. But please is there a way to rectif the problem described above**

Many thanks

-sugz

---

### Post by Sugz on 2008-01-04
Please any help?

---

### Post by Sugz on 2008-01-04
Here is the output /.xsession-errors file from the error message that i described in the first post.

```
[B]/etc/gdm/presession/default: regitering your session with wtmp and utmp
/etc/gdm/presession/default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x " /var/lib/gdm/:0.Xservers" -h " " -l ":0" "myusername"
/etc/gdm/Xsession: Beginning Session Setup...
PRNG is not seeded[/B]
```


Again any help appreciated

---

