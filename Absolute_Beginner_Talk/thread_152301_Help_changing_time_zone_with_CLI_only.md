---
title: "Help changing time zone with CLI only"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by wnb on 2006-03-29
Hi guys-

I need to change the time zone on a Ubuntu server, because Indiana finally is joining the rest of the country in DST.

Unfortuantely, there's no GUI on the box, so I need to do so via command line.

Can somebody please point me in the right direction?

Thanks in advance!

---

### Post by kont.raen on 2006-03-29
[QUOTE=wnb]Hi guys-

I need to change the time zone on a Ubuntu server, because Indiana finally is joining the rest of the country in DST.

Unfortuantely, there's no GUI on the box, so I need to do so via command line.

Can somebody please point me in the right direction?

Thanks in advance![/QUOTE]

Hmmm - my first thought was /etc/timezone - but unfortunately I do not have the time to take a look and play currently... Nevertheless - maybe you could just make the change there and restart the clock service?

---

### Post by siminone on 2006-03-29
not sure about changing time zone but I believe the date command changes date and time.

For info, the following links contains info about bash commands

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.linuxcommand.org/superman_pages.php](http://www.linuxcommand.org/superman_pages.php)

---

### Post by wnb on 2006-03-29
^^^ Thanks, digging through those resources now!

[QUOTE=kont.raen]Hmmm - my first thought was /etc/timezone - but unfortunately I do not have the time to take a look and play currently... Nevertheless - maybe you could just make the change there and restart the clock service?[/QUOTE]

Thanks for the suggestion. I have only a very basic working knowledge of linux, but I've been tasked with this job for today.  If you (or anyone else) wouldn't mind, could you please explain how to restart the clock service? Is it a simple 

```
clock -restart
```

?

Thanks again in advance.

---

### Post by siminone on 2006-03-29
Sorry didn't read thread properly, this webpage details how to change timezone.

[http://linux.co.uk/howtos/TimePrecision-HOWTO/tz.html](http://linux.co.uk/howtos/TimePrecision-HOWTO/tz.html)

---

### Post by ronmarley1 on 2006-03-29
H wnb,
Type ```
sudo tzconfig
``` is a terminal window and follow the prompts.

---

### Post by gregport on 2008-01-25
If tzconfig isn't installed (such as on Ubuntu Server 7.10), the following command will work (found on the tzselect man page):

```

sudo dpkg-reconfigure tzdata

```

---

