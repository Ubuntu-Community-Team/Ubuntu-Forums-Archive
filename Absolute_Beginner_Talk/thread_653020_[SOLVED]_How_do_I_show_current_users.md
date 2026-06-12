---
title: "[SOLVED] How do I show current users ?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by kent41 on 2007-12-29
Hi
I have been away from Ubuntu for about 1 year, but now I am back.

My question is when I use TOP to show task running I see at the very top of the display "2 users". How do I show who are the 2 users?

By the way I am using  7.10
Thanks Kent41

---

### Post by bukwirm on 2007-12-29
The 'who' command gives you information about all users logged in.

---

### Post by kent41 on 2007-12-29
> **bukwirm said:**
> The 'who' command gives you information about all users logged in.

Thanks bukwirm

This is the results I get when using WHO.
```
kent     tty7         2007-12-29 10:32 (:0)
kent     pts/0        2007-12-29 11:48 (:0.0)

```

I think I am tty7 but who is pts/0? Better yet why 2?

---

### Post by tgalati4 on 2007-12-29
If you look at your process list (ps -ef) you will see that you actually have 6 tty consoles open already.  There's a historical reason for these.  You can modify your bootup script to not create these to speed up bootup slightly.  I assume that tty7 is the 7th terminal opened and that is what you logged in with.  I assume the pts is the graphical environment, but I'm not sure where the acronym came from.  The tty is a contraction of teletype, back when these beasts were popular.  Who needs a display when you have a teletype!

Having multiple logged-in users allows you to kill the xserver (when it freezes or acts strange) and still be logged in running all of your important services like printing and file sharing.

To save typing in your busy life, the *what* command gives you load and who is logged on:

>w

---

### Post by scorp123 on 2007-12-29
> **kent41 said:**
>  This is the results I get when using WHO.
```
kent     tty7         2007-12-29 10:32 (:0)
kent     pts/0        2007-12-29 11:48 (:0.0)

```  tty7 is the graphical login screen. Chances are you were logged into your desktop when you ran that command? "pts" are open shell sessions, e.g. "pts/0" is the first terminal app you opened ... e.g. to run the "top" and "who" commands in?

> **kent41 said:**
>  Better yet why 2?  Because technically you opened two terminal sessions. From the system's point of view you're logged in twice, once on your desktop running on tty7 and once into a virtual terminal via an open terminal application. Sample output from my laptop here: ```
scorp      tty7         2007-12-28 18:15 (:0)
scorp      pts/0        2007-12-29 23:05 (:0.0)
scorp      pts/1        2007-12-29 23:43 (:0.0)
scorp      pts/2        2007-12-29 23:44 (pegasus)
``` So I am logged into my desktop on tty7, "gnome-terminal" is open with two tabs (giving me pts/0 and pts/1) and I logged in from another machine with the name "pegasus" (so 'who' is showing this to be a remote connection and displays the hostname "pegasus" where the connection originates from).

You may want to try this variation of the "who" command:  **[COLOR="Red"]w[/COLOR]**  (yes, that's just the letter "w" ...). It gives far far more useful info. Sample output from my laptop here:  ```
23:47:22 up  3:17,  5 users,  load average: 0.32, 0.21, 0.12
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
scorp      tty7     :0               Fri18    1.00s  4:59m  0.51s x-session-manager
scorp      pts/0    :0.0             23:05    6:14m  0.17s  0.17s bash
scorp      pts/1    :0.0             23:43    1.00s  0.18s  0.02s ssh trinity
scorp      pts/2    pegasus          23:44    1.00s  0.17s  0.01s w
```

Try that on your system. I find "w" is less confusing than "who".

---

