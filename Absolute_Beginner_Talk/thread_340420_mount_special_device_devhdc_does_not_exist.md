---
title: "mount: special device /dev/hdc does not exist"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by teletecker on 2007-01-17
Greetings,
When trying to acess cd / dvd drive I get this error. Seen two previous posts with same error and tried everything suggested to no effect. Anyone know what else i can do?
Cheers,

---

### Post by Pobega on 2007-01-17
Type this into the terminal and tell me what you get:> user@ubuntu:~$ dmesg | grep sd

---

### Post by teletecker on 2007-01-17
Forgive my ignorance - like most posting here I'm new to Linux and not very cluey with the terminal.
My several attempts give this response:
idiot@idiot-laptop:~$ user@ubuntu:~$ dmesg | grep sd
bash: user@ubuntu:~$: command not found
idiot@idiot-laptop:~$ ~$ dmesg | grep sd
bash: ~$: command not found
idiot@idiot-laptop:~$ dmesg | grep sd
idiot@idiot-laptop:~$ $ dmesg | grep sd
bash: $: command not found
idiot@idiot-laptop:~$

---

### Post by Ben Sprinkle on 2007-01-17
```

sudo mount -a

```
That mounts all I believe.

---

### Post by Pobega on 2007-01-17
No no, don't copy the user@comp bit ;p

Copy everything after that:> dmesg | grep sd

---

