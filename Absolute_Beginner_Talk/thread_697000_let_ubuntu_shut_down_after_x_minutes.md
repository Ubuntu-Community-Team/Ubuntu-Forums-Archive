---
title: "let ubuntu shut down after x minutes"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-02-14
How can I make ubuntu shut down by itself after x hours?

---

### Post by mkoehler on 2008-02-14
Hey,

If you type the following command into the terminal, it will shut down in XX minutes:

```
sudo shutdown <time>
```

where time is in minutes.

---

### Post by billgoldberg on 2008-02-14
To be clear it would give something like this command

```
sudo shutdown 120
```

this would then should my computer down in 2 hours?

And if I decided to cancel, what command should I use?

---

### Post by nhandler on 2008-02-14
> **billgoldberg said:**
> To be clear it would give something like this command

```
sudo shutdown 120
```

this would then should my computer down in 2 hours?

And if I decided to cancel, what command should I use?

You can learn more about the shutdown command by typing "man shutdown" in a terminal. Based on the man page, you can use "sudo shutdown now" to shutdown now, "sudo shutdown 7:50" to shutdown at 7:50, or "sudo shutdown +120" to shutdown in 120 minutes (I've also seen the last version written as "sudo shutdown now+120").

---

### Post by billgoldberg on 2008-02-14
Thanks buddy, I should really learn more about the cli.

I've took some online courses (I now know how to navigate and copy/cut files in the terminal) but got bored after a while.

---

### Post by ljrossi on 2008-07-08
How do I add this automatcly on star up.

I mean , my kids uses the computer, I whant them to use it only 1 hour. 
So I should add this "shutdown 60" on starting ?

Off course but off topic from this tread will be how to save that it has allready been used 1 hour and should no let it go anymore.

---

### Post by RollingStar on 2008-07-08
Cool, didn't know I could do this with Ubuntu!

---

### Post by NotebookCity on 2008-07-08
Learning more every post I read.  Thanks!

---

### Post by kostkon on 2008-07-08
There is a very good application for doing this, with more options and a GUI; it's called [*GShutdown*]("http://gshutdown.tuxfamily.org") and you can install it from *Synaptic*.

---

