---
title: "Run sudo command at boot"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by meuge on 2007-06-18
Hi

The cpu frequency management on my laptop is a big bugged, and won't set the maximum speed correctly, so I am stuck at 1GHz, when the max is 1.67.

The command:
$ sudo cpufreq-set -u 1.67Ghz

fixes the problem... but it needs to be executed every time I boot up... and it's annoying to have to enter my password. 

Is there any way I can have this command be executed on startup, even though it needs su priviledges?

Thanks in advance...

---

### Post by freakavoid on 2007-06-18
You can try adding an entry in your sudoers file. First backup your sudoers file just to be safe. Then,

```
sudo visudo
```

to edit it.

and add the line

```

%groupname ALL=(root) NOPASSWD: /usr/bin/cpufreq-set

```

at the end of the file. Where groupname is a group you are in (your username will suffice). 

Be careful though. And I think a better solution to this problem can be found. Look up what your governer is with the cpufreq-info command. Try setting it to ondemand.

---

### Post by txgeek on 2007-06-18
Or, you could just add the command to /etc/rc.local

sudo nano -w /etc/rc.local
 cpufreq-set -u 1.67Ghz
<press ctrl-x to save>

---

