---
title: "I installed gdesklets, but all I see is a white window"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-12
Well, some time ago I installed gdesklets, but all I found was a white window. I tried reinstalling, and deleting the contents of $HOME/.gdesklets, without luck. Can someone help me at this?

[IMG]http://img120.imageshack.us/img120/4853/gdeskletslk2.png[/IMG]

---

### Post by overlord.gaurav on 2007-10-12
I have exactly the same problem!
```
overlord@ubuntu:~$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

```

Here's the log file:
```
Log messages of /home/overlord/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[10/13/07-07:25:20]===
Could not import tiling module!


```

Kindly help.

---

### Post by Fixman on 2007-10-13
Um...some help here?
Could it be that I am using a private internet connection?

---

### Post by overlord.gaurav on 2007-10-13
I'm just not able to fix it.
Anyone, help??

---

### Post by Rui Pais on 2007-10-13
hi,
give a look at this [thread here]("http://ubuntuforums.org/showpost.php?p=2839174&postcount=10") to see if it can help you.

Good Luck.

---

### Post by overlord.gaurav on 2007-10-13
Hmm, now it works all fine!
Thanks for your reply!

---

