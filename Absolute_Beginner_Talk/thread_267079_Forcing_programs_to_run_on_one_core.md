---
title: "Forcing programs to run on one core?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by halcyon on 2006-09-28
I've got a dual core processor, but some programs have problems utilizing both cores, so I want to force specific programs to use one core, while the rest continue to use both.  Is there a way or a program that allows me to do this, short of installing a non-dual core kernel?

---

### Post by yota on 2006-09-28
Hi, sure there's a way!

First get the schedutils package:
```

sudo apt-get install schedutils

```
Then have a look at taskset command
```

man taskset

```
I.e. to run 'command' on core 1 only you should do this way:
```

taskset -c 1 command

```

Hope this helps!

---

### Post by fakie_flip on 2007-04-12
Thanks. That worked. How do I check what core processes are running on? The man page was a little confusing to me, and I didn't understand it all. I tried to find out what core xclock is running on by doing this. What is affinity mask? I don't have a third core. I have dual core.

```
chris@ubuntu:~$ xclock &
[1] 26071
chris@ubuntu:~$ taskset -p `pidof xclock`
pid 26071's current affinity mask: 3
chris@ubuntu:~$ taskset -c 1 gedit &
[2] 26509
chris@ubuntu:~$ taskset -p `pidof gedit`
pid 26509's current affinity mask: 2
chris@ubuntu:~$ 
```

---

