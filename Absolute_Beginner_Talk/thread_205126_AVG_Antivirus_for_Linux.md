---
title: "AVG Antivirus for Linux"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Drifter on 2006-06-28
Anyone know how to get the update process to work in avg.  everything else works but the update, this is the message I get:

Update process failed..
Reason: Can not create file '/opt/grisoft/avg7/var/run/avgupdate.pid'.

---

### Post by digimars on 2006-06-28
Did you use [these]("http://www.ubuntuforums.org/showthread.php?t=136064") instructions?  Particularly 7.a?

You could also just run
```

sudo /opt/grisoft/avg7/bin/avgupdate -o

```

---

### Post by Drifter on 2006-06-28
Yes that is what I used, I used b under 7 does that make a difference for updates

---

### Post by Ptero-4 on 2006-06-28
You need to set avg to run through sudo. To do that create a shortcut that runs gksudo followed by the avg binary.

---

### Post by digimars on 2006-06-28
The b option is for a normal user.  Unless this user has root privelages already, I suggest the 'a' option.  If you use the menu entry for 'a', it will still ask you for a password before it proceeds.  But it does work and it will update your definitions that way.

---

### Post by Drifter on 2006-06-28
I don't know how to do that yet, if you could show me a how to on it I would be thankful for it

---

### Post by Drifter on 2006-06-28
Digimars, if I redo the thread I used what will happen to the avg, should I take it off or just rerun the thread.

---

### Post by digimars on 2006-06-28
If you're talking about having a working update button, you don't have to reinstall AVG (I think that's what you're asking?).  Just redo the stuff under 7.a and delete out your menu entries that you created using 7.b for the updater.  Such as mine I have one menu entry under System Tools for AVG (which should be the same as what you already have) but I also have a separate menu entry for AVG Updater that I click, type my password in the console that pops up, then I'm good to go.

---

### Post by Drifter on 2006-06-28
I did 7. a saved everything but I still keep getting the update error above.  Your terminal process does work, I got the updates that way but I can't just click the update button and get them.

---

