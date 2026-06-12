---
title: "[SOLVED] Restrict Computer Access Time"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-12-05
I have a question regarding computer/user access times and durations of access. Are there any ways to restrict these? I have taken a look at the etc/security/time.conf file, but I do not know how to use the commands - that is, do you just run them in terminal? Also, are there any other applications/commands that I can use? Also, how do you undo or change these restrictions in the future?

---

### Post by Dr Small on 2007-12-05
I saw "timeoutd" in synaptic the other day while browsing around.
I never took the time to see how it operated, but it may be worth looking into.

Dr Small

---

### Post by Hospadar on 2007-12-05
are you trying to timeout local sessions or remote sessions (i.e. ssh sessions)

here's some info about ssh timeouts
[http://64.233.167.104/search?q=cache:3zcN3sWMSvAJ:www.experts-exchange.com/Security/Q_20745427.html+set+timeouts+for+ssh+logins&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a](http://64.233.167.104/search?q=cache:3zcN3sWMSvAJ:www.experts-exchange.com/Security/Q_20745427.html+set+timeouts+for+ssh+logins&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a)

(I use the google cache because it's a pay website and I'm super sneaky)

---

### Post by ShadowMKII on 2007-12-05
I thought I had already searched for that in Synaptic at one point, but I guess I was mistaken! It seems to be exactly what I was looking for, but I cannot seem to save the command in the file that is written there. Could I get some help on this? By the way, I am trying to use timeoutd and I have not tried to do this kind of file editing before manually, without copying and pasting, that is. I currently have things set to:

```
# /etc/timeouts: user login/idle/session time limits.  See timeouts(5).
#
# Format:  TIMES:TTYS:USERS:GROUPS:MAXIDLE:MAXSESS:MAXDAY:WARN
#   or:    TIMES:TTYS:USERS:GROUPS:LOGINSTATUS
#
# Some examples:
#
# dopey is not allowed to login
#Al:*:dopey:*:NOLOGIN
#
# cas gets unlimited use
#Al:*:cas:*:0:0:0:0
#
# fred is allowed 20 minutes idle, 240 mins per session, and 480 mins per day
# on ttyS3
#Al:ttyS3:fred:*:20:240:480:10
#
# everyone else is allowed only 120min/session, 240/day
#Al:ttyS3:*:*:20:120:240:5

Al:*:jordi:*:10:60:180:3
```

This is where "Al" symbolizes "all days of the week," "jordi" symbolizes my login name, "10" for the idle time (though I do not know if I need this due to my current settings for my screen saver to apply after 5 minutes of inactivity, "60" being the maximum session time, "180" being the maximum time per day, and "3" being the warning time before I get logged off of my computer. I do not know if this will work - please help!!

---

### Post by ShadowMKII on 2007-12-06
Is anyone able to assist?

---

