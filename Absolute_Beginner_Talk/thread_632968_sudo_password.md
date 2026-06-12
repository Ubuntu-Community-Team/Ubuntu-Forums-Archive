---
title: "sudo password"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by prospero96 on 2007-12-06
I'm getting frustrated using terminal commands.
I type sudo password and a prompt says "password:" but I can't enter any data (the cursor doesn't move).
What am I doing wrong?:confused:

---

### Post by bodhi.zazen on 2007-12-06
if you use sudo you will not see your typing reflected on the monitor.

Just use sudo before your command, and enter your password, hit enter.

---

### Post by AndyLovesLinux on 2007-12-06
> **prospero96 said:**
> I'm getting frustrated using terminal commands.
I type sudo password and a prompt says "password:" but I can't enter any data (the cursor doesn't move).
What am I doing wrong?:confused:

example
sudo apt-get install xmms
password: 
 enter password up there ^^ it will not echo the password, hit enter and poof command is executing :guitar:

---

### Post by igknighted on 2007-12-06
> **prospero96 said:**
> I'm getting frustrated using terminal commands.
I type sudo password and a prompt says "password:" but I can't enter any data (the cursor doesn't move).
What am I doing wrong?:confused:

It is typing, you just can't see it.  Kind of a pain, but I would bet that it's a security thing (anything printed to the terminal could conceivably give hints to a hacker as to what your password is).

---

### Post by subs on 2007-12-06
*sudo* and *su* dont echo the password

---

### Post by Joeb454 on 2007-12-06
They aren't meant to. Like Andy said, it doesn't move for security reasons.

So you are typing, e.g. if your password is 1234 then

```
sudo apt-get install ubuntu-restricted-extras
[sudo] password for user: 1234
```

would output
```
sudo apt-get install ubuntu-restricted-extras
[sudo] password for user: 
```

---

