---
title: "Running GUI based system configuration application remotely"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by redr on 2007-06-01
When I run commad like 'sudo synaptic &' It asks for password, but password appears in plain text.
If I don't give '&', it works but then I don't get shell prompt back.:(
I connect to the system remotely using 'ssh -X'
Is it a bug?
Please help.
thanks.

---

### Post by Cypher on 2007-06-01
You have two options here.

Option 1
```

sudo su
synaptic &
exit

```

Option 2
```

sudo synaptic
CTRL-Z
bg

```
What you're doing in the second method is running the application, providing your password, but since you don't have the "&" there, it will run in foreground. When you hit CTRL-Z, it stops the foreground process and drops you to the shell. Then typing "bg" will put the, now stopped, foreground process into the background and allow it to continue to execute while you have access to the shell again.

Having said all that, for this very unique situation just as long as you do ALL the commands in Option 1, that might be your best option.

---

### Post by jd65pl on 2007-06-01
Do you get anything different if you use

```
gksudo synaptic &
```

---

### Post by redr on 2007-06-04
gksudo worked. Thanks a lot.

But then ```
sudo synaptic &
``` should give some warning. Because, it does ask for password, which appears in plain text on screen.  and eventually the job gets stopped.

---

