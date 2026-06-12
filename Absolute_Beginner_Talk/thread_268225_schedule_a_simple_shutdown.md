---
title: "schedule a simple shutdown"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Anonii on 2006-09-29
Whats the easiest way to schedule a shutdown? I have no idea of cron daemons etc, and if they are useful in this situation.  I just want my Ubuntu to shutdown automatically in an hour. I know there is a parameter in the shutdown command doing that, but I had zero success on understanding it.

Thanks!

---

### Post by skymt on 2006-09-29
```
sudo shutdown -P 60
```Replace 60 with whatever you want (in minutes).

---

### Post by mitch.c on 2006-09-29
> **Anonii said:**
> Whats the easiest way to schedule a shutdown? I have no idea of cron daemons etc, and if they are useful in this situation.  I just want my Ubuntu to shutdown automatically in an hour. I know there is a parameter in the shutdown command doing that, but I had zero success on understanding it.

Thanks!
If you want to do it w/o cron (which would schedule it at a fixed interval), type this in a terminal:
```
# schedules shutdown (power off) in 60 minutes
sudo shutdown -hP 60 &

# to cancel...
sudo shutdown -c
```

---

### Post by Drakkor on 2006-09-29
Or,to set a specified time use:
```
sudo shutdown -h 23:00 &

```
which would shut it down at 11:00pm

---

### Post by skymt on 2006-09-30
> **mitch.c said:**
> If you want to do it w/o cron (which would schedule it at a fixed interval), type this in a terminal:
```
# schedules shutdown (power off) in 60 minutes
sudo shutdown -hP 60 &

# to cancel...
sudo shutdown -c
```

](*,) Yes, you need -P. My mistake. I'll edit my original post. However, you don't need both -h and -P. So: "sudo shutdown -P 60 &".

---

### Post by mitch.c on 2006-09-30
> **skymt said:**
> ](*,)However, you don't need both -h and -P. So: "sudo shutdown -P 60 &".

Hmm. That's funny, on my box I need the -h option; without it I get:
```
mitch@ubuntu:~$ sudo shutdown -P 60 &
mitch@ubuntu:~$ shutdown: -H and -P flags needs -h flag.
```

As long as I can remember, and through several distros, that's how it's always been. Am I missing something?

---

### Post by skymt on 2006-09-30
> **mitch.c said:**
> Hmm. That's funny, on my box I need the -h option; without it I get:
```
mitch@ubuntu:~$ sudo shutdown -P 60 &
mitch@ubuntu:~$ shutdown: -H and -P flags needs -h flag.
```

As long as I can remember, and through several distros, that's how it's always been. Am I missing something?

[quote=man shutdown]       -P, --poweroff
              Requests  that  the system be powered off after it has been brought down.  init(8) will generate the power-off event once the
              shutdown event has been processed.[/quote]
The manpage says nothing about that. I guess it's just bad documentation. So, -hP it is. Sorry 'bout that.

---

### Post by Anonii on 2006-10-01
Thank you all <:

---

