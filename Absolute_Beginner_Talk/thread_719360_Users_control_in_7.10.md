---
title: "Users control in 7.10"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by momist on 2008-03-09
Today I have tried to add a new user, for the first time.  Going into System:Administration:Users and Groups, I added a user, and gave them a password.  Everything seemed to work OK.  I then thought that I should give them some permissions, so I went into System:Administration:Users and Groups:Manage Groups.  When changing permissions there, I found that my own entry had no permissions for anything, and whenever I changed any group to give them permissions, all the groups became duplicated throughout the list.  I ended up with 20 'sets' of groups, with root and all the other groups continually repeated.  Is this normal?  :confused:

---

### Post by hyper_ch on 2008-03-09
I don't think it is... please post this:

```

cat /etc/passwd

```

```

cat /etc/groups

```

---

### Post by momist on 2008-03-10
Thanks for looking at this hyper_ch


OK, here goes:
```

ian@attercop:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:109::/var/run/dbus:/bin/false
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:106:114:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:107:116:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
gdm:x:108:118:Gnome Display Manager:/var/lib/gdm:/bin/false
ian:x:1000:1000:Ian M. Stewart,,,:/home/ian:/bin/bash
ntp:x:109:120::/home/ntp:/bin/false
linda:x:1001:1001:Linda Stewart,,,,:/home/linda:/bin/bash

```

and 
```

ian@attercop:~$ cat /etc/groups
cat: /etc/groups: No such file or directory

```

oops!

HTH

---

### Post by bodhi.zazen on 2008-03-10
Just cat /etc/group (no "s" on the end)

```
sudo cat /etc/group
```

And, yea, this has been reported as a bug, but I do not know the solution. Try searching the forums for duplicate users or duplicate groups ....

---

### Post by momist on 2008-03-10
> **bodhi.zazen said:**
> 
And, yea, this has been reported as a bug, but I do not know the solution. Try searching the forums for duplicate users or duplicate groups ....

Thanks for that bodhi.zazen

Since it's a known bug, and doesn't seem to be detrimental to anything I'm now trying to do, I'll leave it there.  I don't suppose that I should flag this thread [SOLVED] though.

---

### Post by bodhi.zazen on 2008-03-10
As long as there are not multiple users / groups in those files I think you are fine (it is a bug in the gui).

If you want to mark this as solved :

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And, no, I can not find the bug report ATM :(

---

