---
title: "Where do I find the boot log"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-04-17
Hey Team,

How do I see the boot log so I can diagnose an error I am having that I only see during boot?

Thanks,
Will

---

### Post by dstew on 2007-04-17
One way is by opening a terminal and entering at the command prompt:

dmesg | less

That shows the messages of each kernel component and module as they go in.

---

### Post by willz06jw on 2007-04-17
Thanks again,

That shows most of the startup jazz, but it doesn't show the hard drive sector errors it seems to be finding during boot.  Strange.

Will

---

### Post by RedSquirrel on 2007-04-17
If you want to save the output of dmesg as a text file, just do:

```
dmesg > dmesg.txt
```and it will be saved as dmesg.txt in the directory where you executed that command (somewhere under your home directory is best, obviously).

If your drive errors are not in there, you can also have a look at:

```
more /var/log/fsck/checkfs
```and 

```
more /var/log/fsck/checkroot
```

---

### Post by Cypher on 2007-04-17
You can also check out "/var/log/messages" which contains all messages across multiple-boots. If you don't find the messages you are looking for, then check out other files in "/var/log". It's possible that SYSLOG may be configured to send messages to different files..

Regards

---

### Post by willz06jw on 2007-04-19
Thanks to both of you and specifically RedSquirrel, I found my hard drive errors that show up every time at boot using:

```
more /var/log/fsck/checkfs
```

Now to start up a new thread about the hard drive problem : /

Thanks again,
Will

---

### Post by RedSquirrel on 2007-04-19
Glad I could help.

The new "hard drive problem" thread is [here]("http://ubuntuforums.org/showthread.php?t=413280"), for anyone else reading this "boot log" thread.  ;)

---

