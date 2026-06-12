---
title: "Stability"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by dragn on 2007-07-31
I was performing a dvd rip and left the system unattended.. when I came home system was hard locked.
Recovered by using system disk and using it's "safe mode" but now only core programs run and anything under Wine or Cedega locks up the system.

Could I have been hacked?:lolflag:

---

### Post by irish_flu on 2007-07-31
That's not good.  Any chance your hard drive is (almost) full?

---

### Post by dragn on 2007-08-01
I still have 21gig's free

---

### Post by Seisen on 2007-08-01
See if you can pull up the logs, they should provide some type of information that might be the cause.

The logs are located in ```
/var/log
```

---

### Post by dragn on 2007-08-01
All I can say is that was bad!
The hard drive itself went bad I couldn't even reformat it.
Lost a tone of stuff but    IIIMMMEE BBAAAAACCCKKK hehe:guitar:

---

### Post by earobinson on 2007-08-01
all I can tell u is that the odd of you being hacked are about 1 in 100000

---

### Post by dragn on 2007-08-01
Well considering the fact the the HD is less than 6 months old and it was a fresh install I was kinda hoping it was a hack instead of costing me money.
But I am just glad to be up and running again haha:guitar:

Crash the Gates and smash the Windows

---

### Post by dragn on 2007-08-02
I managed to access the bad drive by connecting it as external to my new linux box.
I recovered most of my files but cant seem to find my received e-mail.

---

### Post by Seisen on 2007-08-02
Did you ever pull up the logs and see what caused the problem?

---

### Post by MrPotatoHead on 2007-08-02
> **Seisen said:**
> Did you ever pull up the logs and see what caused the problem?


Hello, can you give simple instructions about how to access such logs? Thanks.

---

### Post by asmoore82 on 2007-08-02
? You wouldn't just happen to have an nVidia GeForce Graphics card would you ??

---

### Post by Seisen on 2007-08-02
Well there are two ways. 

1.)Go to System<Administration<System Log
or 
2.)You can open up a terminal and go to /var/log and type in **ls** and this will show you every log that is in the /var/log directory. Then to open the log up just 

```
text editor /var/log/whicheverlog
``` Just change text editor to what every one you wan to use such as gedit, kate, vim, nano, etc...

For example say I want to check out my system logs using vim. I would put this in the terminal.

```
vim /var/log/syslog
```

---

### Post by dragn on 2007-08-04
As a matter of fact I do have an NVIDIA PCI Express..should I be concerned?




Crash the Gates and smash the Windows

---

### Post by RudolfMDLT on 2007-08-04
you emails, if you have been using evolution will be here:

/home/rudolf/.evolution

where rudolf should be replaced by your username.

Copy the entire folder to save mail settings, contacts and mail.

---

