---
title: "login &quot;impossible&quot;"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by swisscoach on 2006-11-26
Hello
I've search for some similar problems, but can't completely understand/resolve it.
Yesterday, I shut down normally, but this morning it won't log me in. Reason is out of disk space on /home. OK. I've made 2GB of space in console mode. And reboot. When I log in now, what I have is only a console in the upper left (without border). I can launch whatever program I want, konqueror in which i post this message... :-k 

For context i'm running Kubuntu edgy, Radeon driver, Beryl not enabled on boot (I have to launch it manually).

I don't know what to look for to solve the situation.

Thank's for help, tips
David
PS: Sorry if my English is not "perfect". :p

---

### Post by taurus on 2006-11-26
What's the output of this command from a terminal?

```
df -h
```

---

### Post by swisscoach on 2006-11-26
> **taurus said:**
> What's the output of this command from a terminal?

```
df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.8G  2.6G  6.7G  28% /
varrun                252M   76K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   7% /lib/modules/2.6.17-10-generic/volatile
/dev/sda5              14G  8.6G  4.0G  69% /home
/dev/sda1              18G  7.7G  9.5G  45% /media/sda1
/dev/sda6              14G   13G  1.2G  92% /media/sda6

I was at 98% on /home before I free up some space...

---

### Post by taurus on 2006-11-26
See which directory takes up all the space with

```
du
```

---

### Post by swisscoach on 2006-11-26
> **taurus said:**
> See which directory takes up all the space with

Now I have some space (~4Gb). The only full partition (sda6) is a Fat32 partition only used for storage. (sda1) is Xp, NTFS. My "/home" (69%) is also on another partition than "/" (28%). Don't think it's space anymore...

looking in log files... kdm.log is empty but syslog show me this:
```

Nov 26 10:13:35 swisscoach-laptop kdm_greet[4273]: Can't open default user face
Nov 26 10:13:44 swisscoach-laptop kdm_greet[4273]: Internal error: memory corruption detected
Nov 26 10:13:44 swisscoach-laptop kdm: :0[4476]: Cannot create session log file .xsession-errors: Permission denied
Nov 26 10:15:28 swisscoach-laptop kdm_greet[4663]: Can't open default user face
Nov 26 10:15:52 swisscoach-laptop kdm_greet[4663]: Internal error: memory corruption detected
Nov 26 10:15:52 swisscoach-laptop kdm: :0[4679]: Cannot create session log file .xsession-errors: Permission denied

```

---

### Post by taurus on 2006-11-26
Yip.  I see that your /dev/sda6 is filling up fast while /dev/sda1 is about half full (or half empty, whichever way you fancy).  Just watch what you save to /home/$HOME because if you run out of space in your $HOME partition, you can't log in...

---

### Post by swisscoach on 2006-11-26
Resolved: found this thread
[http://ubuntuforums.org/showthread.php?t=229938]("http://ubuntuforums.org/showthread.php?t=229938")

had to ```
chmod 666 /lib/udev/devices/null
```
don't know why, but it does the job. Any idea ?

By the way, is it possible to have something giving me a warning when my /home become full ? and another partition, etc...

Thanks for help

---

