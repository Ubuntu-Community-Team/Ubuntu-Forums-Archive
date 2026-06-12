---
title: "Remote session help"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-08-21
I was wondering if it is possible to do the following:

1. Login to computer with SSH (putty)
2. Start a bf2 dedicated server
3. Log out of session and leave bf2 server running.


:-k 


Cheers.

---

### Post by reclusivemonkey on 2006-08-21
> **Scorpuk said:**
> I was wondering if it is possible to do the following:

1. Login to computer with SSH (putty)
2. Start a bf2 dedicated server
3. Log out of session and leave bf2 server running.


Yes! The application you need is called "screen". I don't run a BF2 server, but I use it to run my CS:Source server. The following is what I use; you should be able to modify it easily enough to run a BF2 server;

```

#!/bin/sh
echo "Starting Cs:Source Server"
sleep 1
screen -A -m -d -S css-server ./srcds_run -ip 192.168.1.5 -port 27015 -console -game cstrike +map de_aztec +maxplayers 16 -tickrate 66 -autoupdate

```

Once you have started screen, open it up with the name you used after "-S", so in this case its;

```

screen -x css-server

```

to close the "screen" without closing the application, use CTRL+a+d. You'll see "[detached]" at the console to confirm that everything's OK. The man page for screen should tell you all you need to know. HTH :)

---

### Post by Scorpuk on 2006-08-22
Thanx reclusivemonkey your coding work wonders

```
screen -A -m -d -S bf2-server ./start.sh +dedicated +lowPriority
```

Used the above and looked as though nothing had happened, but used

```
screen -ls
```

and there it was...

> 
john@silverstone:~$ screen -ls
There is a screen on:
        2895.bf2-server (Detached)
1 Socket in /var/run/screen/S-john.


Then logged out of remote session and logged back in and it was still there.


cheers,

John.

---

