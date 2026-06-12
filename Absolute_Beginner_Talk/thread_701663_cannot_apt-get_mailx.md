---
title: "cannot apt-get mailx?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by DrObviousSo on 2008-02-19
I'm trying to setup mailx on my machine, since apparently I can use it to send mail from the command line.  I tried searching for it in synaptic, but no returns.

> drobvious@uKermit:~$ mailx
The program 'mailx' can be found in the following packages:
 * mailx
 * mailutils
Try: sudo apt-get install <selected package>
bash: mailx: command not found
drobvious@uKermit:~$ sudo apt-get mailx
E: Invalid operation mailx
drobvious@uKermit:~$ 


I'm using x64, if that matters.  Any suggestions on how I can get mailx setup would be appreciated.

---

### Post by neurostu on 2008-02-19
try:
```

$sudo apt-get ** install** mailx

```

---

### Post by neurostu on 2008-02-19
Also if you want to check to see if the ubuntu repositories even contain the program/package you are looking for try:

```

aptitude search <program name>

returns:

user@host$ aptitude search mailx
p   mailx                           - A simple mail user agent 
user@host$

```

This is a great way to look for packages and to get the exact name before you install.

---

### Post by DrObviousSo on 2008-02-19
well, don't I feel like an idiot.  Thanks!

---

### Post by neurostu on 2008-02-19
Don't worry "apt-get" confused us all at one time,

---

### Post by lespaul_rentals on 2008-02-19
> **neurostu said:**
> Don't worry "apt-get" confused us all at one time,

Never confused me.  :p

[/sarcasm]

---

