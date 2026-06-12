---
title: "Cron, Zenity, and Xorg don't play nice."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by JetSirus on 2007-05-28
Ok, I am trying to set up a cron job that will use zenity to pop up a warning box.  The problem as far as I can tell is that all cron jobs run in the background, so when zenity is invoked it doesn't know what xorg "screen" to display on.  Does anyone know how to specify a screen for it to use?

Thanks in advance for any help.

P.S.
Here is the full cron command.
```
0 4	* * *	root zenity --warning --title "Computer Restarting" --text "System restarting for daily maintenance in one minute." && shutdown +1 -r "Restart in one minute."
```

---

### Post by JetSirus on 2007-05-29
Giving this a bump in hopes of a solution.

---

### Post by lambros on 2007-05-29
This might be helpful:
[http://doc.gwos.org/index.php/Cron_GUI](http://doc.gwos.org/index.php/Cron_GUI)

Lambros

---

### Post by JetSirus on 2007-05-29
> **lambros said:**
> This might be helpful:
[http://doc.gwos.org/index.php/Cron_GUI](http://doc.gwos.org/index.php/Cron_GUI)

Lambros

You are a lifesaver!

---

