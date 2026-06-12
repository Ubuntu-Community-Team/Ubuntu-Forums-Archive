---
title: "verifying if gift daemon is running"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by ubiubi on 2008-01-01
How do i verify if there is another gift deamon running on the host?

---

### Post by llamakc on 2008-01-01
If the daemon is named giftd, run:

```

ps aux | grep [g]iftd

```

If nothing is returned, it is not running.

---

### Post by capink on 2008-01-01
or:

```
ps -C gift
```

if you want non zero exit code when the daemon is not running.

---

### Post by ubiubi on 2008-01-01
mark@mark-desktop:~$ ps aux | grep {g]iftd
mark      7103  0.0  0.1   2976   752 pts/0    R+   19:46   0:00 grep {g]iftd
mark@mark-desktop:~$ ps aux | grep {g]iftd
mark      7106  0.0  0.1   2976   748 pts/0    R+   19:47   0:00 grep {g]iftd
mark@mark-desktop:~$ ps -c gift
ERROR: Unsupported option (BSD syntax)
 
I'm trying to run apollon and it refuses to connect. When I run giftd I'm told to check if another daemon application is already running and if port 1213 is running. I did a check on the ports using sudo tcpdump -i etho port 1213 and I got a message sying hardware does not exist!

I've really no ideas!

---

### Post by Dr Small on 2008-01-01
Maybe that should have been?
```
sudo tcpdump -i eth0 port 1213
```

---

### Post by llamakc on 2008-01-01
> **ubiubi said:**
> mark@mark-desktop:~$ ps aux | grep {g]iftd
mark      7103  0.0  0.1   2976   752 pts/0    R+   19:46   0:00 grep {g]iftd
mark@mark-desktop:~$ ps aux | grep {g]iftd
mark      7106  0.0  0.1   2976   748 pts/0    R+   19:47   0:00 grep {g]iftd
mark@mark-desktop:~$ ps -c gift
ERROR: Unsupported option (BSD syntax)
 
I'm trying to run apollon and it refuses to connect. When I run giftd I'm told to check if another daemon application is already running and if port 1213 is running. I did a check on the ports using sudo tcpdump -i etho port 1213 and I got a message sying hardware does not exist!

I've really no ideas!

You have typos on both suggestions. It's brackets around the g in my suggestion and a capitalized C on the other suggestion.

so 

ps -C gift

or

ps aux | grep [g]iftd

---

### Post by ubiubi on 2008-01-01
mark@mark-desktop:~$ sudo tcpdump -i eth0 port 1213
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

mark@mark-desktop:~$ ps aux | grep [g]iftd
mark      7099  0.0  0.6   5640  3144 ?        S    19:45   0:00 giftd

could somebody please help explain how this might explain my problem? thanks for everybody's time and patience

---

