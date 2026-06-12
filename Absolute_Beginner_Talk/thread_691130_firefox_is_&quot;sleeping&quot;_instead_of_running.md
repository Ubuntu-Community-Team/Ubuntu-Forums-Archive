---
title: "firefox is &quot;sleeping&quot; instead of running"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by BeardedOne on 2008-02-08
Firefox was running fine in my new install of Gutsy.  Now, when I try to open it I get the "start new or restore old" message.  When I choose either one, I get the message that Firefox needs a reboot or end process.  When I check the system monitor, I find Firefox is there, but 'sleeping'. I reboot, restart, and it sleeps again. I end process, restart, and it sleeps again.  I used synaptics to reinstall - same result.  I did a complete removal and installed again - the same. My guess is that Firefox is still referencing something corrupted, but I don't know how to get to it to erase it (since complete removal didn't work). I'm new to Linux and don't know where things are stored or even what I'm looking for. Any ideas?

Thanks.

---

### Post by aeiah on 2008-02-08
how odd. open up a terminal window (accessories>terminal) and launch firefox from there (type firefox and press enter). the terminal window should log any and all errors. maybe that'll make things clearer. paste what the terminal says in here and we'll have a look at it

---

### Post by jan quark on 2008-02-08
1. try a complete removal using
```

sudo dpkg --purge firefox
```

2.run firefox through the terminal like aeiah has suggested

3. did this happen only with firefox or with any other web browser, too?

---

### Post by nemilar on 2008-02-08
The above posts have good ideas.  I would add that you might also try :

```
mv ~/.mozilla ~/mozilla_backup
```

Perhaps there's a corrupt file somewhere in there that is freaking out Firefox.

---

### Post by BeardedOne on 2008-02-08
I tried running firefox from the terminal and the cursor just sits and blinks at me - no firefox, no errors, no message.

Tried "mv ~/.mozilla ~/mozilla_backup" from the terminal and it fixed the problem.

Thanks everyone.

Special thanks to Nemilar for a successful fix.

---

