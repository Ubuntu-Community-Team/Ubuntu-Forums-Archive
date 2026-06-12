---
title: "how to identify a process"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-08-14
i was trying to read a CD
However the OS (for whatever reason) could not read the CD, but seems to have entered into a endless loop

CD Eject is also not functioning as the volume is in use message prompts up

How do i identify this process and kill it

i have htop installed

pkj

---

### Post by RomeReactor on 2007-08-14
Hi. I've had that happen to me a couple of times; particularly with scratched CDs getting stuck while trying to read. Try killing Nautilus from the System Monitor, sometimes that stops the CD. You could also try to stop it by restarting X pressing CTRL+ALT+BACKSPACE.

Most of the times, however, I just had to resort to a reboot. Hopefully someone will post a better solution.

---

### Post by yellowband on 2007-08-14
if you can get a terminal open, you can have a look at your process with 

ps -e

if you find one you know is the bad process, try

kill -9 <process id number>

---

### Post by pkj on 2007-08-14
I am able to identify the process but unable to kill it.....

pkj

---

### Post by pkj on 2007-08-14
Unable to kill the process with kill -9 (pid) command

System monitor showing the process status as "interruptible"

pkj

---

### Post by iver2435 on 2007-08-14
try pre-pending "sudo" in front of the command, like so:

```
sudo kill -9 <process id number>
```

---

### Post by colo on 2007-08-14
You can determine which processes have an open file-descriptor on mounted media, and are therefore preventing it from being unmounted, with the `fuser`-command.

Let's assume your CD is mounted to "/media/cdrom", then you'd issue

```

fuser -m /media/cdrom

```

THis will yield somethink similar to
```

colo@zealot ~ $ fuser -m /media/cdrom
/media/cdrom:        889c   914c  1219c  1681c  1684c  1694c

```

The numeric part of the output is a list of PIDs (Process IDentificators) that refer to processes you need to terminate (or at least have them stop maintaining a file decriptor, thereby open()ing something on your device) to make unmount work.

A quick, yet brutal way to handle this automatically is:
```

for process in $(fuser -m /home 2>/dev/null | egrep "[[:space:] ]"); do kill "${process}"; done

```

Replace `kill` by `kill -9` in the above one-liner to send the even more aggressive SIGKILL instead of SIGTERM. (check `man 7 signal` for more information).
You can also use `lsof` instead of `fuser` to check for file handles.

Another way of relentlessly unmounting is called "lazy umount". Google should yield info on that one for you, too.

Hth.

---

